

<template>

<div class="corpo">
  <h1 class="centralizado">{{tituloPagina}}</h1>

  <input type="search" class="filtro" @input= "filtro = $event.target.value" placeholder="filtre pelo título da foto">
  <ul class="lista-fotos">
    <li class="lista-fotos-item" v-for="foto of fotosComFiltro">
      <meu-painel :titulo="foto.titulo">
        <imagem-responsiva :url= "foto.url" :titulo= "foto.titulo"></imagem-responsiva>
      </meu-painel>
    </li>
  </ul>

</div>

</template>





<script>

import Painel from './components/shared/painel/Painel.vue';
import ImagemResponsiva from './components/shared/imagem-responsiva/ImagemResponsiva.vue';


export default {

  components: {

    'meu-painel' : Painel,
    'imagem-responsiva' : ImagemResponsiva,

  },


  computed: {

    fotosComFiltro(){

      if(this.filtro){

        let exp = new RegExp(this.filtro.trim(), 'i');

        return this.fotos.filter(foto => exp.test(foto.titulo));

      } else {

        return this.fotos;


      }

    }

  },

  data () {
    return {
      tituloPagina: 'AluraPics',
      fotos: [],
      filtro: ''
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

 .filtro {
    display: block;
    width: 100%;
  }


.corpo {

font-family: Helvetica, sans-serif;
margin: 0 auto;
width: 88%;

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
