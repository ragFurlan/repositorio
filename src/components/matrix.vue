<template>
  <div>
    <label
      v-if="alertando"
      style="index: 100; position: absolute; background: yellow; height: 20px;"
    >Você ganhou parabéns!!!</label>
    <table class="table">
      <tr>
        <td @click="jogar(0)" ref="A1"></td>
        <td @click="jogar(1)" ref="B1"></td>
        <td @click="jogar(2)" ref="C1"></td>
        <td @click="jogar(3)" ref="D1"></td>
        <td @click="jogar(4)" ref="E1"></td>
        <td @click="jogar(5)" ref="F1"></td>
        <td @click="jogar(6)" ref="G1"></td>
        <td @click="jogar(7)" ref="H1"></td>
        <td @click="jogar(8)" ref="I1"></td>
        <td @click="jogar(9)" ref="J1"></td>
        <td @click="jogar(10)" ref="K1"></td>
      </tr>
      <tr>
        <td @click="jogar(0)" ref="A2"></td>
        <td @click="jogar(1)" ref="B2"></td>
        <td @click="jogar(2)" ref="C2"></td>
        <td @click="jogar(3)" ref="D2"></td>
        <td @click="jogar(4)" ref="E2"></td>
        <td @click="jogar(5)" ref="F2"></td>
        <td @click="jogar(6)" ref="G2"></td>
        <td @click="jogar(7)" ref="H2"></td>
        <td @click="jogar(8)" ref="I2"></td>
        <td @click="jogar(9)" ref="J2"></td>
        <td @click="jogar(10)" ref="K2"></td>
      </tr>
      <tr>
        <td @click="jogar(0)" ref="A3"></td>
        <td @click="jogar(1)" ref="B3"></td>
        <td @click="jogar(2)" ref="C3"></td>
        <td @click="jogar(3)" ref="D3"></td>
        <td @click="jogar(4)" ref="E3"></td>
        <td @click="jogar(5)" ref="F3"></td>
        <td @click="jogar(6)" ref="G3"></td>
        <td @click="jogar(7)" ref="H3"></td>
        <td @click="jogar(8)" ref="I3"></td>
        <td @click="jogar(9)" ref="J3"></td>
        <td @click="jogar(10)" ref="K3"></td>
      </tr>
      <tr>
        <td @click="jogar(0)" ref="A4"></td>
        <td @click="jogar(1)" ref="B4"></td>
        <td @click="jogar(2)" ref="C4"></td>
        <td @click="jogar(3)" ref="D4"></td>
        <td @click="jogar(4)" ref="E4"></td>
        <td @click="jogar(5)" ref="F4"></td>
        <td @click="jogar(6)" ref="G4"></td>
        <td @click="jogar(7)" ref="H4"></td>
        <td @click="jogar(8)" ref="I4"></td>
        <td @click="jogar(9)" ref="J4"></td>
        <td @click="jogar(10)" ref="K4"></td>
      </tr>
      <tr>
        <td @click="jogar(0)" ref="A5"></td>
        <td @click="jogar(1)" ref="B5"></td>
        <td @click="jogar(2)" ref="C5"></td>
        <td @click="jogar(3)" ref="D5"></td>
        <td @click="jogar(4)" ref="E5"></td>
        <td @click="jogar(5)" ref="F5"></td>
        <td @click="jogar(6)" ref="G5"></td>
        <td @click="jogar(7)" ref="H5"></td>
        <td @click="jogar(8)" ref="I5"></td>
        <td @click="jogar(9)" ref="J5"></td>
        <td @click="jogar(10)" ref="K5"></td>
      </tr>
      <tr>
        <td @click="jogar(0)" ref="A6"></td>
        <td @click="jogar(1)" ref="B6"></td>
        <td @click="jogar(2)" ref="C6"></td>
        <td @click="jogar(3)" ref="D6"></td>
        <td @click="jogar(4)" ref="E6"></td>
        <td @click="jogar(5)" ref="F6"></td>
        <td @click="jogar(6)" ref="G6"></td>
        <td @click="jogar(7)" ref="H6"></td>
        <td @click="jogar(8)" ref="I6"></td>
        <td @click="jogar(9)" ref="J6"></td>
        <td @click="jogar(10)" ref="K6"></td>
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
      jogando: false,
      casasPrenchidas: [],
      historico: [],
      tempo: 1000,
      alertando: false
    };
  },
  methods: {
    jogar(coluna) {
      let count = 1;
      const elemento = this.$el;
      const thisJogar = this;

      if (!this.jogando && this.podeJogar) {
        this.jogando = true;
        let jogador = "jogador-amarelo";

        setTimeout(function() {
          setClass(0, coluna, jogador);
          setTimeout(function() {
            setClass(1, coluna, jogador);
            if (!verificaSeEstaPreenchida(1, coluna, jogador)) {
              setClass(0, coluna, "neutro");
            }
            setTimeout(function() {
              setClass(2, coluna, jogador);
              if (!verificaSeEstaPreenchida(2, coluna, jogador)) {
                setClass(1, coluna, "neutro");
              }
              setTimeout(function() {
                setClass(3, coluna, jogador);
                if (!verificaSeEstaPreenchida(3, coluna, jogador)) {
                  setClass(2, coluna, "neutro");
                }
                setTimeout(function() {
                  setClass(4, coluna, jogador);
                  if (!verificaSeEstaPreenchida(4, coluna, jogador)) {
                    setClass(3, coluna, "neutro");
                  }
                  setTimeout(function() {
                    setClass(5, coluna, jogador);
                    if (!verificaSeEstaPreenchida(5, coluna, jogador)) {
                      setClass(4, coluna, "neutro");
                    }
                  }, 400);
                }, 400);
              }, 400);
            }, 400);
          }, 400);
        }, 400);
      }

      function setClass(linha, coluna, nome) {
        count++;
        elemento.children[0].childNodes[linha].childNodes[
          coluna
        ].className = nome;

        if (count === 12) {
          // Jogar(getRandom(0, 10), "jogador-vermelho");
          thisJogar.jogando = false;
        }
      }

      function verificaSeEstaPreenchida(linha, coluna, jogador) {
        var preenchida = thisJogar.casasPrenchidas.filter(casa => {
          return casa.linha === linha && casa.coluna === coluna;
        });

        if (preenchida.length === 0 && linha !== 5) {
          return false;
        } else if (preenchida.length === 0 && linha === 5) {
          thisJogar.casasPrenchidas.push({
            linha: linha,
            coluna: coluna,
            jogador: jogador
          });

          if (verificaQuatroSeguidas(linha, coluna, jogador)) {
            thisJogar.jogando = false;
            thisJogar.casasPrenchidas = [];
            thisJogar.alertando = true;
            setTimeout(function() {
              thisJogar.alertando = false;
            }, 1000);
            limparSeleções();
          }
        } else {
          thisJogar.casasPrenchidas.push({
            linha: linha - 1,
            coluna: coluna,
            jogador: jogador
          });

          if (verificaQuatroSeguidas(linha - 1, coluna, jogador)) {
            thisJogar.jogando = false;
            thisJogar.casasPrenchidas = [];
            thisJogar.alertando = true;
            setTimeout(function() {
              thisJogar.alertando = false;
            }, 1000);
          }

          thisJogar.jogando = false;
          return true;
        }
      }

      function limparSeleções() {
        const colunas = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11];
        const linhas = [0, 1, 2, 3, 4, 5];

        colunas.forEach(function(coluna) {
          linhas.forEach(function(linha) {
            setClass(linha, coluna, "neutro");
          });
        });

        setClass(0, coluna, "neutro");
      }

      function verificaQuatroSeguidas(linha, coluna, jogador) {
        // const colunas = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11];
        // const linhas = [0, 1, 2, 3, 4, 5];

        var preenchidas = thisJogar.casasPrenchidas.filter(casa => {
          return casa.jogador === jogador;
        });

        if (preenchidas.length < 4) {
          return false;
        } else {
          const colunaEsquerda = [coluna - 1, coluna - 2, coluna - 3];
          const colunaDireita = [coluna + 1, coluna + 2, coluna + 3];
          const colunaIntermediaria1 = [coluna - 1, coluna + 1, coluna + 2];
          const colunaIntermediaria2 = [coluna - 1, coluna - 2, coluna + 1];

          const linhaAcima = [linha - 1, linha - 2, linha - 3];
          const linhaAbaixo = [linha + 1, linha + 2, linha + 3];
          const linhaIntermediaria3 = [linha - 1, linha + 1, linha + 2];
          const linhaIntermediaria4 = [linha - 1, linha - 2, linha + 1];

          let esquerda = 0;
          let direita = 0;
          let inter1 = 0;
          let inter2 = 0;
          let inter3 = 0;
          let inter4 = 0;
          let acima = 0;
          let abaixo = 0;

          preenchidas.forEach(function(item) {
            if (
              item.linha == linha &&
              (item.coluna === colunaEsquerda[0] ||
                item.coluna === colunaEsquerda[1] ||
                item.coluna === colunaEsquerda[2])
            ) {
              esquerda++;
            }

            if (
              item.linha == linha &&
              (item.coluna === colunaDireita[0] ||
                item.coluna === colunaDireita[1] ||
                item.coluna === colunaDireita[2])
            ) {
              direita++;
            }

            if (
              item.linha == linha &&
              (item.coluna === colunaIntermediaria1[0] ||
                item.coluna === colunaIntermediaria1[1] ||
                item.coluna === colunaIntermediaria1[2])
            ) {
              inter1++;
            }

            if (
              item.linha == linha &&
              (item.coluna === colunaIntermediaria2[0] ||
                item.coluna === colunaIntermediaria2[1] ||
                item.coluna === colunaIntermediaria2[2])
            ) {
              inter2++;
            }

            if (
              item.coluna == coluna &&
              (item.linha === linhaAcima[0] ||
                item.linha === linhaAcima[1] ||
                item.linha === linhaAcima[2])
            ) {
              acima++;
            }

            if (
              item.coluna == coluna &&
              (item.linha === linhaAbaixo[0] ||
                item.linha === linhaAbaixo[1] ||
                item.linha === linhaAbaixo[2])
            ) {
              abaixo++;
            }

            if (
              item.coluna == coluna &&
              (item.linha === linhaIntermediaria3[0] ||
                item.linha === linhaIntermediaria3[1] ||
                item.linha === linhaIntermediaria3[2])
            ) {
              inter3++;
            }

            if (
              item.coluna == coluna &&
              (item.linha === linhaIntermediaria4[0] ||
                item.linha === linhaIntermediaria4[1] ||
                item.linha === linhaIntermediaria4[2])
            ) {
              inter4++;
            }
          });

          if (
            esquerda > 2 ||
            direita > 2 ||
            inter1 > 2 ||
            inter2 > 2 ||
            inter3 > 2 ||
            inter4 > 2 ||
            acima > 2 ||
            abaixo > 2
          ) {
            return true;
          } else {
            return false;
          }
        }
      }

      // function getRandom(min, max) {
      //   min = Math.ceil(min);
      //   max = Math.floor(max);
      //   return Math.floor(Math.random() * (max - min + 1)) + min;
      // }
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