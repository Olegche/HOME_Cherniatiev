<template>
  <div>
    <span>
      Serve
      <ol>
        <li v-for="(item, index) in serveList" :key="index">
          {{ item }}
          <button @click="$emit('eat', index)">Eat</button>
        </li>
      </ol>
    </span>
  </div>
</template>

<script>
export default {
  name: "serve",
  props: {
    serveList: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="scss" scoped>
</style>