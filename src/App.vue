<template>
  <div id="app">
    <div class="tudo">
      <div class="titulo">
        <p>Jogo ForInline</p>
      </div>
      <div class="coluna1">
        <div class="matrix">
          <matrix :podeJogar="podeJogar"></matrix>
        </div>
        <div class="botoes">
          <botao nomeId="0" @jogar="jogar()"></botao>
        </div>
      </div>
      <div class="coluna2">
        <div class="listaAcoes"></div>
      </div>
      <div class="coluna3">
        <div class="dicas"></div>
        <div class="timeLine"></div>
      </div>
    </div>
  </div>
</template>

<script>
import matrix from "./components/matrix.vue";
import botao from "./components/botao.vue";

export default {
  name: "app",
  components: {
    matrix,
    botao
  },
  props: {
    podeJogar: Boolean
  },
  methods: {
    jogar() {
      this.podeJogar = !this.podeJogar;
    }
  }
};
</script>

<style>
.titulo {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-size: 1.2em;
  font-weight: 600;
  margin-left: 20px;
}
.tudo {
  height: 530px;
  width: 96%;
  background: lightgray;
  padding-right: 30px;
  padding-left: 30px;
  padding-bottom: 20px;
  padding-top: 20px;
}
.coluna1 {
  width: 54%;
  height: 440px;
  float: left;
  padding: 5px;
}
.coluna2 {
  width: 10%;
  height: 450px;
  float: left;
  padding: 5px;
}
.coluna3 {
  width: 32%;
  height: 440px;
  float: left;
  padding: 5px;
}
.matrix {
  border: 1px;
  border-radius: 1%;
  border-color: black;
  background: white;
  width: 100%;
  height: 80%;
  margin-bottom: 10px;
}

.botoes {
  border: 1pz;
  border-radius: 1%;
  border-color: black;
  background: white;
  width: 100%;
  height: 20%;
  margin-top: 10px;
}

.listaAcoes {
  border: 1pz;
  border-radius: 1%;
  border-color: black;
  background: white;
  width: 100%;
  height: 100%;
}

.dicas {
  border: 1pz;
  border-radius: 1%;
  border-color: black;
  background: white;
  width: 100%;
  height: 20%;
  margin-bottom: 10px;
}

.timeLine {
  border: 1pz;
  border-radius: 1%;
  border-color: black;
  background: white;
  width: 100%;
  height: 80%;
  margin-top: 10px;
}
</style>
