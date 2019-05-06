<template>
  <div>
    <button @click="click($event)">{{nomeBotao}}</button>
  </div>
</template>

<script>
export default {
  props: ["nomeBotao"],
  methods: {
    click() {
      event.preventDefault();
      this.$emit("click");
    }
  }
};
</script>

<style scoped>
</style>