<template>
  <div>
    <span>
      Cooking
      <ol>
        <li v-for="(item, index) in cookingList" :key="index">
          {{ item }}
          <button @click="$emit('dish-to-serve', index)">to serve</button>
        </li>
      </ol>
    </span>
  </div>
</template>

<script>
export default {
  name: "cooking",
  props: {
    cookingList: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="scss" scoped>
</style>