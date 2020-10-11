<template>
  <div>
    <span>
      Orders
      <ol>
        <li v-for="(item, index) in orderList" :key="index">
          {{ item }}
          <button @click="$emit('dish-to-cooking', index)">to cooking</button>
        </li>
      </ol>
    </span>
  </div>
</template>

<script>
export default {
  name: "order",
  props: {
    orderList: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="scss" scoped>
</style>

