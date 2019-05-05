<template>
  <div>
    <table class="table">
      <tr>
        <td @click="jogar(0)" ref="A1"></td>
        <td @click="jogar(1)" ref="B1"></td>
        <td @click="jogar(2)" ref="C1"></td>
        <td @click="jogar(3)" ref="D1"></td>
        <td @click="jogar(4)" ref="E1"></td>
        <td @click="jogar(5)" ref="F1"></td>
        <td @click="jogar(7)" ref="G1"></td>
        <td @click="jogar(8)" ref="H1"></td>
        <td @click="jogar(9)" ref="I1"></td>
        <td @click="jogar(10)" ref="J1"></td>
        <td @click="jogar(11)" ref="K1"></td>
      </tr>
      <tr>
        <td @click="jogar(0)" ref="A2"></td>
        <td @click="jogar(1)" ref="B2"></td>
        <td @click="jogar(2)" ref="C2"></td>
        <td @click="jogar(3)" ref="D2"></td>
        <td @click="jogar(4)" ref="E2"></td>
        <td @click="jogar(5)" ref="F2"></td>
        <td @click="jogar(7)" ref="G2"></td>
        <td @click="jogar(8)" ref="H2"></td>
        <td @click="jogar(9)" ref="I2"></td>
        <td @click="jogar(10)" ref="J2"></td>
        <td @click="jogar(11)" ref="K2"></td>
      </tr>
      <tr>
        <td @click="jogar(0)" ref="A3"></td>
        <td @click="jogar(1)" ref="B3"></td>
        <td @click="jogar(2)" ref="C3"></td>
        <td @click="jogar(3)" ref="D3"></td>
        <td @click="jogar(4)" ref="E3"></td>
        <td @click="jogar(5)" ref="F3"></td>
        <td @click="jogar(7)" ref="G3"></td>
        <td @click="jogar(8)" ref="H3"></td>
        <td @click="jogar(9)" ref="I3"></td>
        <td @click="jogar(10)" ref="J3"></td>
        <td @click="jogar(11)" ref="K3"></td>
      </tr>
      <tr>
        <td @click="jogar(0)" ref="A4"></td>
        <td @click="jogar(1)" ref="B4"></td>
        <td @click="jogar(2)" ref="C4"></td>
        <td @click="jogar(3)" ref="D4"></td>
        <td @click="jogar(4)" ref="E4"></td>
        <td @click="jogar(5)" ref="F4"></td>
        <td @click="jogar(7)" ref="G4"></td>
        <td @click="jogar(8)" ref="H4"></td>
        <td @click="jogar(9)" ref="I4"></td>
        <td @click="jogar(10)" ref="J4"></td>
        <td @click="jogar(11)" ref="K4"></td>
      </tr>
      <tr>
        <td @click="jogar(0)" ref="A5"></td>
        <td @click="jogar(1)" ref="B5"></td>
        <td @click="jogar(2)" ref="C5"></td>
        <td @click="jogar(3)" ref="D5"></td>
        <td @click="jogar(4)" ref="E5"></td>
        <td @click="jogar(5)" ref="F5"></td>
        <td @click="jogar(7)" ref="G5"></td>
        <td @click="jogar(8)" ref="H5"></td>
        <td @click="jogar(9)" ref="I5"></td>
        <td @click="jogar(10)" ref="J5"></td>
        <td @click="jogar(11)" ref="K5"></td>
      </tr>
      <tr>
        <td @click="jogar(0)" ref="A6"></td>
        <td @click="jogar(1)" ref="B6"></td>
        <td @click="jogar(2)" ref="C6"></td>
        <td @click="jogar(3)" ref="D6"></td>
        <td @click="jogar(4)" ref="E6"></td>
        <td @click="jogar(5)" ref="F6"></td>
        <td @click="jogar(7)" ref="G6"></td>
        <td @click="jogar(8)" ref="H6"></td>
        <td @click="jogar(9)" ref="I6"></td>
        <td @click="jogar(10)" ref="J6"></td>
        <td @click="jogar(11)" ref="K6"></td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    podeJogar: Boolean
  },
  data() {
    return {
      jogando: false
    };
  },
  methods: {
    jogar(coluna) {
      const elemento = this.$el;
      const thisJogar = this;

      if (!this.jogando && this.podeJogar) {
        var jogadores = ["jogador-amarelo", "imagem-vermelha"];

        jogadores.forEach(function(jogador) {
          coluna = jogador == "imagem-vermelha" ? getRandom(0, 10) : coluna;
          thisJogar.jogando = true;
          let count = 1;

          setTimeout(function() {
            setClass(0, coluna, jogador);
            setTimeout(function() {
              setClass(1, coluna, jogador);
              setClass(0, coluna, "neutro");
              setTimeout(function() {
                setClass(2, coluna, jogador);
                setClass(1, coluna, "neutro");
                setTimeout(function() {
                  setClass(3, coluna, jogador);
                  setClass(2, coluna, "neutro");
                  setTimeout(function() {
                    setClass(4, coluna, jogador);
                    setClass(3, coluna, "neutro");
                    setTimeout(function() {
                      setClass(5, coluna, jogador);
                      setClass(4, coluna, "neutro");
                      setTimeout(function() {
                        setClass(6, coluna, jogador);
                        setClass(5, coluna, "neutro");
                      }, 500);
                    }, 500);
                  }, 500);
                }, 500);
              }, 500);
            }, 500);
          }, 500);

          function setClass(linha, coluna, nome) {
            count++;
            elemento.children[0].childNodes[linha].childNodes[
              coluna
            ].className = nome;

            if (count === 12) {
              thisJogar.jogando = false;
            }
          }
        });
      }
      function getRandom(min, max) {
        min = Math.ceil(min);
        max = Math.floor(max);
        return Math.floor(Math.random() * (max - min + 1)) + min;
      }
    }
  },
  watch: {
    isChange: function() {},
    methods: {}
  }
};
</script>

<style scoped>
.table {
  width: 100%;
  height: 353px;
  background-image: url("../assets/imagens/fundo_matrix.jpg");
  border-radius: 1%;
}

td {
  background-image: url("../assets/imagens/centro_matrix.png");
}

.neutro {
  background-image: url("../assets/imagens/centro_matrix.png");
}

.jogador-amarelo {
  background-image: url("../assets/imagens/centro_amarelo_matrix.png");
}

.jogador-vermelho {
  background-image: url("../assets/imagens/centro_vermelho_matrix.png");
}
</style>