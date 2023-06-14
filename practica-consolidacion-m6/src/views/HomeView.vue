<template>
  <div class="home">
    <card-home-vue :games="juegos"></card-home-vue>
    <button @click="getData" v-if="juegos.length!=0" class="btn btn-success mb-5" type="button" >Ver más</button>


    
  </div>
</template>

<script>
import axios from 'axios'
import CardHomeVue from '@/components/CardHome.vue'

export default {
  name: 'HomeView',
  created(){
    this.getData()
  },
  data() {
    return {
      API_KEY:'4e8d239de81246c7afdc25dafac8404b',
      juegos:[],
      page:1,
    }
  },
  methods:{
    getData(){
      axios
      .get(`https://api.rawg.io/api/games?key=${this.API_KEY}&page=${this.page}`)
      .then(json=>{
        let results=json.data.results
        results.forEach(juego => {
            this.juegos.push(juego)
        });
        this.page++
        // this.juegos=json.data.results
        // console.log(this.juegos)
})
    }
  },
  components: {
    CardHomeVue,
  }
}
</script>
