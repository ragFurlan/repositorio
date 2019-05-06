
<script>
import botao from "./botao.vue";
export default {
  extends: botao,
  props: ["direcao"],
  methods: {
    click() {
      event.preventDefault();
      this.$emit("click", this.direcao);
    }
  }
};
</script>

<style  scoped>
</style>