<template>
  <div>
    <button @click="jogar($event)">INICIAR</button>
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