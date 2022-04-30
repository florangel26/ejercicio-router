<template>
 <Titulo texto="titulo de componente view que esta seguido / de otro componente view" /> 
  <h2>ID :{{ $route.params.id }}</h2>
  <h3>{{articulo.title}}</h3>
  <p>{{articulo.body}}</p>
  </template>

<script>
import Titulo from '../components/Titulo.vue'

export default {
  components: {
    Titulo
  },
  data() {
    return {
       articulo: {}
    }
  },
  methods:{
      async consumirArticulo(){
        try{
          const data = await fetch (`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
          const objeto = await data.json()
          this.articulo = objeto
        }catch(error){
          console.log(error)
        }
      }
    },

    created(){
      this.consumirArticulo()
    }
  
}
</script>

<style>

</style>