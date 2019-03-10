

<template>

<div class="corpo">
  <h1 class="centralizado">{{tituloPagina}}</h1>

  <ul class="lista-fotos">
    <li class="lista-fotos-item" v-for="foto of fotos">
      <meu-painel :titulo="foto.titulo">
          <img class="imagem-responsiva" :src="foto.url" :alt="foto.titulo">
      </meu-painel>
    </li>
  </ul>

</div>

</template>





<script>

import Painel from './components/shared/painel/Painel.vue';


export default {

  components: {

    'meu-painel' : Painel,
  },

  data () {
    return {
      tituloPagina: 'AluraPics',
      fotos: []
    }
  },

  created() {

    this.$http.get('http://localhost:3000/v1/fotos')
    .then(res => res.json())
    .then(fotos => this.fotos = fotos, err => console.log(err));

  }

}

</script>

<style scoped>


.corpo {

font-family: Helvetica, sans-serif;
margin: 0 auto;
width: 88%;

}

.imagem-responsiva {

  width: 100%;
}

.centralizado {

  text-align: center;

}

.lista-fotos-item {

  display: inline-block;
  list-style: none;

}

.painel {

  box-shadow: 5px 5px 5px black;
}

</style>
