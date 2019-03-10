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
      tituloPagina: 'Pagina de teste',

     fotos: [
       {
       url: 'https://abrilexame.files.wordpress.com/2016/09/size_960_16_9_passarinho1.jpg',
       titulo: 'passarinho1'
       },
      {
        url: 'https://www.petz.com.br/blog/wp-content/uploads/2017/07/passarinhos02.jpg',
        titulo: 'passarinho2'
      }
     ]
    }
  }
}

</script>

<style>



</style>
