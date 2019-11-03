<template>
  <div class="global">
    <form action="#" class="form">
        <input type="text" v-model="search" class="form-search-input" placeholder="Informe sua busca">
        <button @click="pesquisar" class="form-search-button"> Pesquisar </button>
    </form>
    <div class="result">
      <h3>{{ result.title }}</h3>
      <p>{{ result.description }}</p>
    </div>
  </div>
</template>

<script>

import axios from 'axios'

export default {
  name: 'Form',
  data(){
    return{
      search: '',
      result: {
        title: null,
        description: null
      }
    }
  },
  methods:{
    pesquisar(){

      axios
      .get(`http://127.0.0.1:5000/${this.search}`)
      .then(response => {
        this.result.title = response.data.title;
        this.result.description = response.data.description;
      })
        
    }
  }
}
</script>


<style scoped>


.global{
  width: 600px;
  height: 500px;
  background-color: #eee;
  text-align: center;
  vertical-align: center;
  margin: 50px auto 0;
  filter: drop-shadow(5px 5px 5px #ccc);
  border-radius: 10px;
}

.form{
  width: 100%;
  height: 60px;
  background-image: linear-gradient(to bottom, #5ec, #0aa) ;
  padding-top: 10px;
  border-radius: 10px 10px 0px 0px;
}

.form-search-input{
  width: 200px;
  height: 20px;
  margin: 10px;
  border-radius: 10px;
  border: #fff 2px solid;
  background-color: transparent;
  color: #fff;
  padding: 5px 10px;
  font-size: 16px;
}

.form-search-input::placeholder{
  color: #fff;
}

.form-search-button{
  height: 30px;
  width: 100px;
  background-color: transparent;
  color: #fff;
  border: #fff 2px solid;
  border-radius: 10px;
  font-size: 14px;
}

.result{
  width: 90%;
  margin: 0 auto;
  font-family: sans-serif;
  color: #333;
  line-height: 25px;
}



</style>
