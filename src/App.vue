<template>
  <div id="app">
    <div class="tudo">
      <div class="titulo">
        <p>Jogo ForInline</p>
      </div>
      <div class="coluna1">
        <div class="matrix">
          <matrix
            :podeJogar="podeJogar"
            @atualizarHistorico="atualizarHistorico"
            :limpar="limpar"
            :parar="parando"
            :continuar="continuando"
            :moverEsquerda="moverEsquerda"
            :moverDireita="moverDireita"
          ></matrix>
        </div>
        <div class="botoes">
          <div>
            <botao :nome-botao="nomeBotao" @click="jogar()"></botao>
          </div>
          <div>
            <botao nome-botao="LIMPAR" @click="limparJogo()"></botao>
          </div>
        </div>
      </div>
      <div class="coluna2">
        <div class="listaAcoes">
          <botao nome-botao="PARAR" @click="parar()"></botao>
          <botao nome-botao="CONTINUAR" @click="continuar()"></botao>
          <botao-direcao direcao="esquerda" :nome-botao="esquerda" @click="mover"></botao-direcao>
          <botao-direcao direcao="direita" :nome-botao="direita" @click="mover"></botao-direcao>
        </div>
      </div>
      <div class="coluna3">
        <div class="dicas scroll">
          <b>1- Objetivo: alinhar 4 jogadas</b>
          <br>
          <b>2- Para jogar clique na coluna</b>
          <br>
          <b>3- Clique no botão iniciar antes de começar o jogo</b>
          <br>
          <b>4- Caso queira mudar o curso da jogada. Clica em parar e depois para esquerda e direira, após posicionar é só clicar em continuar</b>
        </div>
        <div class="timeLine scroll">
          <timeLine :listaHistorico="listaHistorico"></timeLine>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import matrix from "./components/matrix.vue";
import botao from "./components/botao.vue";
import timeLine from "./components/timeLine.vue";
import botaoDirecao from "./components/botaoDirecao.vue";

export default {
  name: "app",
  components: {
    matrix,
    botao,
    timeLine,
    botaoDirecao
  },
  props: {
    podeJogar: Boolean,
    limpar: Boolean,
    parando: Boolean,
    moverEsquerda: String,
    moverDireita: String,
    continuando: String
  },
  data() {
    return {
      listaHistorico: [],
      nomeBotao: "INICIAR",
      nomeBotaoParar: "PARAR",
      esquerda: "<= ESQUERDA",
      direita: "DIREITA =>"
    };
  },
  methods: {
    jogar() {
      this.podeJogar = !this.podeJogar;
      if (this.podeJogar) {
        this.listaHistorico.push({ historico: "Jogo Iniciado" });
        this.nomeBotao = "BLOQUEAR";
      } else {
        this.listaHistorico.push({ historico: "Jogo Terminado" });
        this.nomeBotao = "INICIAR";
      }
    },
    atualizarHistorico(historico) {
      if (historico == null || historico == undefined) {
        this.listaHistorico = [];
      } else {
        this.listaHistorico.push(historico);
      }
    },
    limparJogo() {
      this.limpar += "A";
    },
    parar() {
      this.parando += "A";
    },
    continuar() {
      this.continuando += "A";
    },
    mover(direcao) {
      if (direcao == "esquerda") {
        this.moverEsquerda += "1";
      } else {
        this.moverDireita += "1";
      }
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

.scroll {
  overflow: scroll;
}
</style>
