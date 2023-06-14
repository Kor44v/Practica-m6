<template>
  <div>
    <div class="container">
      <div class="row mt-3">
        <div class="col-4">
          <h2>{{juego.name_original}}</h2>
          <div class="p-3">
            <h5>Sitio oficial </h5>
            <a :href="juego.website">{{juego.website}}</a>
          </div>
          <h4 class="mt-5">Plataformas disponibles</h4>
          <div v-for="(plataforma, index) in juego.parent_platforms" :key="index" class=" p-3 fs-6 text-start d-inline-block">
            <div v-for="(platform,index) in plataforma" :key="index">
              {{platform.name}}
            </div>
          </div>

        </div>
        <div class="col">
          <img :src="juego.background_image" class="img-fluid rounded shadow" alt="">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "game-comp",
  created() {
    this.getEspecificCharacter(this.id)
  },
  data() {
    return {
        API_KEY:'4e8d239de81246c7afdc25dafac8404b',
        juego:{}
        }
    },
  props: ['id'],
  methods: {
    getEspecificCharacter(id){
      axios
      .get(`https://api.rawg.io/api/games/${id}?key=${this.API_KEY}`)
      .then(resp=>{
        this.juego=resp.data

      })
    }
  },
};
</script>

<style lang="scss" scoped></style>