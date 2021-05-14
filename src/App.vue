<template>
<div class="container_main">

<h1 class="text">My Pictures</h1>

<div class="container_main___src">

    <v-text-field
    class="container_main___src___input"
      label="Informe os Dados"
      :rules="rules"
      hide-details="auto"
      v-model="msg"
    ></v-text-field>
    {{msg}}

</div>

<div class="container">

 <v-card class="container__card" v-for="(photo, index ) in photos"  :key="index"
    max-width="344">
    <Card  :title="photo.titulo"
        :url="photo.url"
    />

  </v-card>
</div>
</div>

</template>

<script>

import axios from 'axios'
import Card from './components/Card'

export default {
  name: 'App',

  components: {
    Card
  },

  data: () => ({
    photos: [],
    rules: [
      value => !!value || 'Campo não pode ser vazio',
      value => (value && value.length >= 3) || 'Min 3 characters'
    ],

    msg: ''

  }),

  created () {
    axios.get('http://localhost:3000/v1/fotos')
      .then(res => {
        console.log(res.data)
        this.photos = res.data
      })
      .catch(err => {
        console.error(err)
      })
  } // ciclo de vida que cria a app

}
</script>

<style scoped>

.container_main{

    display: flex;
    flex-direction: column;
    align-items: center;
}

.container_main___src{
    display: flex;
    flex-direction: column;
    width: 100%;
    align-items: center;
}
.container_main___src___input{
    width: 50%;
}
.container{

  display: flex;
  flex-wrap: wrap;
  width: 100%;
  justify-content:center;

}

.container__card{
display: flex;
flex-direction: column;
width: 20rem;
margin: 2%;

}

.container__input{
width: 50%;
height: 25px;align-content: center;
}

.container__src{
    display: flex;
    width: 100%;
    height: 100px;
    background: chocolate;
}

.text{
    color: coral;
    text-align: center;
}

</style>
