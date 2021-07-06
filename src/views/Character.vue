<template>
  <div clas="container">
    <h1 class="text-center">Datos de Usuario</h1>
      <img :src="personaje.image" class="card-img-top" alt="">
      <h1>Nombre: {{personaje.name}}</h1>
      <h2>Status: {{personaje.status}}</h2>
      <h2>Genero: {{personaje.gender}}</h2>
      <h2>Especie: {{personaje.species}}</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      personaje: [],
    }
  },
  methods: {
    async consumirPersonaje() {
      try {
        const data = await fetch(`https://rickandmortyapi.com/api/character/${this.$route.params.id}`);
        const getPersonaje = await data.json();
        this.personaje = getPersonaje;
        console.log(this.personaje);
      } catch (error){
        console.log(error);
      }
    }
  },
  created() {
    this.consumirPersonaje();
  }
}
</script>

<style scoped>

</style>