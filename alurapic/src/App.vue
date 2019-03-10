<template>

<div>


<div class="corpo">
  <h1 class="centralizado">{{tituloPagina}}</h1>
  <ul class="lista-fotos">
    <li class="lista-fotos-item" v-for="foto of fotos">
      <img :src="foto.url" :alt="foto.titulo">
    </li>
  </ul>


</div>


</div>


</template>

<script>
export default {
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


<style>


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


</style>
