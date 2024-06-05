<script setup>
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
</script>

<template>
  <h1>{{ dizOla('paula') }}</h1>
  <img v-if="gostaDaGoogle":src="imagemDoGoogle" alt="">
  <img v-else-if="gostaDoBing":src="imagemDoBing" alt="">
  <h2 v-else>Não curte o Google e o Bing </h2>

  <h1 v-if="estaAutorizado">Bem-vindo</h1>
  <h1 v-else>Não possui acesso</h1>

  <button :disabled="botaoEstaDesabilitado">enviar mensagem</button>
</template>

<style scoped>

img {
  max-width: 200px;
}
</style>
