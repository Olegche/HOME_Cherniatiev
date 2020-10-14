<template>
  <div :class="statusClass">
    <div class="title">
      <span>{{ task }}</span>
      <span>{{ time }}</span>
    </div>

    <div class="btns">
      <button @click="$emit('done')">done</button>
      <button @click="$emit('plan')">plan</button>
      <button @click="$emit('postponed')">do late </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDoItem",

  props: {
    id: {
      type: [String, Number],
    //   required:true,  <- Missing required prop: "id" !!!
    default: 6,
    },
    task: {
      type: String,
      default: null,
    },
    time: {
      type: String,
      default: null,
    },
    status: {
      type: String,
      default: null,
    },
  },

  computed: {
    statusClass() {
      switch (this.status) {
        case "NEW":
          return "new";
        case "DONE":
          return "done";
        case "POSTPONED":
          return "postponed";
        case "PLAN":
          return "plan";

        default:
          return "new";
      }
    },
  },
};
</script>

<style lang="css" scoped>
.new {
  color: green;
}
.plan {
  color: yellow;
}
.postponed {
  color: red;
}
.done {
  color: rgb(90, 172, 226);
}
</style>