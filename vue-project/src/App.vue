<script setup>
import { reactive } from 'vue';

const nome = 'Rodrigo Cinelli'
const meuObj = {
  nome: 'Rodrigo Cinelli',
  filmeFavorito: 'Matrix'
}

function dizOla(nome) {
  return `${nome} diz oi!`;
}

const imagemDoGoogle = 'https://www.google.com.br/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png';
const imagemDoBing = 'https://netexperts.com.br/wp-content/uploads/2023/12/bing-p-optimized.webp';

const botaoEstaDesabilitado = false;

const gostaDaGoogle = false;
const gostaDoBing = false;

const estaAutorizado = false;

// let contador = 0;
const estado = reactive({
  contador: 0,
  email: '',
  saldo: 5000,
  transferindo: 0
});

function incrementar() {
  estado.contador++;
}

function decrementar() {
  estado.contador--;
}

function alteraEmail(event) {
  estado.email = event.target.value;
}

function mostraSaldoFuturo() {
  const { saldo, transferindo } = estado;
  return saldo - transferindo;
}

function validaValorTransferencia() {
  const { saldo, transferindo } = estado;
  return saldo >= transferindo;
}

</script>

<template>
  <h1>{{ dizOla('paula') }}</h1>
  <img v-if="gostaDaGoogle" :src="imagemDoGoogle" alt="">
  <img v-else-if="gostaDoBing" :src="imagemDoBing" alt="">
  <h2 v-else>Não curte o Google e o Bing </h2>

  <h1 v-if="estaAutorizado">Bem-vindo</h1>
  <h1 v-else>Não possui acesso</h1>

  <button :disabled="botaoEstaDesabilitado">enviar mensagem</button>

  <br />
  <hr />

  {{ estado.contador }}

  <button @click="incrementar" type="button">+</button>
  <button @click="decrementar" type="button">-</button>

  <br />
  <hr />

  {{ estado.email }}

  <input type="email" @keyup="alteraEmail">

  <br />
  <hr />

  Saldo: {{ estado.saldo }} <br />
  Trasferindo: {{ estado.transferindo }} <br />
  Saldo depois da transferência: {{ mostraSaldoFuturo() }} <br />
  <input class="campo" :class="{ invalido: !validaValorTransferencia() }" @keyup="evento => estado.transferindo = evento.target.value" type="number" placeholder="Quantia para transferir" />
  <button v-if="validaValorTransferencia()">Transferir</button>
  <span v-else>Valor maior que o saldo</span>

</template>

<style scoped>

img {
  max-width: 200px;
}

.invalido {
  outline-color: red;
  border-color: red;
}

.campo {
  border: 2px solid #000;
}

</style>
