<script>
export default {
  props: ['item'],
  setup(props, {emit}) {
    const remove = () => emit('remove');

    return {
      remove
    };
  }
}
</script>

<template>
  <input type="checkbox" v-model="item.done" />
  <span :class="{ inactive: item.done }">{{ item.name }}</span>
  <button @click="remove">Remove</button>
</template>

<style scoped>
  .inactive {text-decoration: line-through; color: gray;}
</style>
