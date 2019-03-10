<template>

<div>


<div>
  <h1>{{tituloPagina}}</h1>
  <li v-for="foto of fotos">
     <img :src="foto.url" :alt="foto.titulo">
  </li>
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
</style>
