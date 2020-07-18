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
  <div :class="{ inactive: item.done }">
    <input type="checkbox" v-model="item.done" />
    {{ item.name }}
    <button @click="remove">Remove</button>
  </div>
</template>

<style scoped>
  .inactive {text-decoration: line-through; color: gray;}
</style>
