<template>
  <div class='container mt-5'>
    <div class="row">
      <div v-for="personaje in personajes.results" :key="personaje.id" class="card col-12 col-sm-4 col-md-3">
        <img :src="personaje.image" class="card-img-top" alt="">
        <div class="card-body">
          <h5 class="card-title">{{personaje.name}}</h5>
          <router-link :to="`/character/${personaje.id}`" class="btn btn-primary">Ir a personaje</router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  components: {},
  data() {
    return {
      personajes: [],
      comentarios: []
    }
  },
  methods: {
      async consumirPersonajes() {
        try {
          const data = await fetch('https://rickandmortyapi.com/api/character');
          const getPersonajes = await data.json();
          this.personajes = getPersonajes;
          console.log(this.personajes);
        } catch (error){
          console.log(error);
        }
      }
  },
  created() {
    this.consumirPersonajes();
  }
}
</script>
