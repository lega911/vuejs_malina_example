<script>
import { ref, computed } from 'vue'
import Item from './Item.vue'
export default {
  components: {
      Item
  },
  setup() {
    let todos = ref([])
    let name = ref('')
    let completed = computed(() => todos.value.filter(i => i.done).length )

    const add = () => {
      if(!name.value) return;
      todos.value.push({name: name.value});
      name.value = '';
    };

    const remove = (i) => {
      todos.value.splice(i, 1);
    };

    return {
      todos,
      name,
      add,
      remove,
      completed
    }
  }
}
</script>

<template>
  <input type="text" v-model="name" @keyup.enter="add" /> <br/>

  <template v-for="(item, index) in todos">
    {{index}}:
    <item :item="item" @remove="remove(index)"></item>
    <br/>
  </template>

  <template v-if="todos.length">
    Completed {{completed}} of {{todos.length}}
  </template>
  <template v-else>
    No tasks yet
  </template>
</template>

<style scoped>
  input {background-color: rgb(147, 208, 236); margin-bottom: 16px;}
</style>
