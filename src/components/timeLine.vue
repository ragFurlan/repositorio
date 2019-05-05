<template>
  <div>
    <p v-for="(value, index) in listaHistorico" :key="index">
      <b v-text="index + ' - ' + value.historico"></b>
    </p>
  </div>
</template>

<script>
export default {
  props: {
    listaHistorico: []
  }
};
</script>

<style scoped>
</style>