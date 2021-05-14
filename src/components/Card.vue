<template>
 <v-card
    class="mx-auto "
    max-width="344"
  >
    <v-img
    :src="url"
      height="200px"
    ></v-img>

    <v-card-title class="container__card___title">
        {{title}}
    </v-card-title>
  </v-card>

</template>
<script>

export default {
  name: 'App',
  props: {
    title: String,
    url: String
  }

}
</script>

<style scoped>

.container__card{
margin: auto;
margin-bottom: 25px;
width: 20rem;
display: flex;
flex-direction: column;

}

.container__card___title{
  display: flex;
  justify-content: center;
  text-transform: uppercase;
}
.container__card___title:hover{
    color: rgb(89, 190, 190);
    cursor: pointer;
}
</style>
