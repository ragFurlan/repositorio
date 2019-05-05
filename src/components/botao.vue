<template>
  <div>
    <button @click="jogar($event)">GO</button>
  </div>
</template>

<script>
export default {
  methods: {
    jogar() {
      event.preventDefault();
      this.$emit("jogar");
    }
  }
};
</script>

<style scoped>
</style>