<template>
<titulo texto="este es el titulo de Blog"/> 
<!--<button @click="consumirApi"> Consumiendo API</button>-->
<div v-for="item in arrayBlog" :key="item.id">
<router-link :to="`/Blog/${item.id}`" >
    {{ item.title }}
</router-link>
</div>
</template>

<script>
import Titulo from '../components/Titulo.vue'
export default {
  components: {
    Titulo
  },
  data() {
    return {
      arrayBlog:[] 
    }
  },
  methods:{
    async consumirApi(){
           try {
             const  data = await fetch('https://jsonplaceholder.typicode.com/posts')
             const  json = await data.json()
             console.log(json)
             this.arrayBlog = json;
           } catch (error) {
             console.log(error)
           } 
    }
  },
  created(){
    this.consumirApi()
  }
}
</script>

<style>
ul{
  list-style: none;
}
</style>