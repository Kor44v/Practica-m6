<template>
  <div>
      <div class="row justify-content-center">
      <div class="col-sm-4 justify-content-center display">
        <div v-for="(juego,index) in games" :key="index"   class="card m-4">
          <div @click="redirectTo(juego.id)" class="card text-start shadow jover" style="width: 18rem;">
            <img :src="juego.background_image" class="card-img-top"  style="object-fit:cover;height:200px" alt="...">
            <div class="card-body" style="height:88px">
              <h5 class="card-title">{{juego.name}}</h5>
            </div>
            <ul class="list-group list-group-flush">
              <li class="list-group-item">Rating: {{juego.rating }}</li>
              <li class="list-group-item">Released:{{juego.released}}</li>
              <li class="list-group-item">Update:{{juego.updated}}</li>
            </ul>
            <div class="card-body">
              <button type="button" class="btn btn-primary px-4 me-3">Opinar</button>
                <i class="fa-solid fa-heart fa-lg heart" style="color: #ff0000;"></i>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "cards-comp",
  created() {},
  data() {
    return {};
  },
  props: {
    games:{
      type:Array,
      required:true
    }
  },
  methods: {
    redirectTo(i){
      this.$router.push(`/juego/${i}`)
    }
  },
  components:{
  }
};
</script>
<style  scoped>
.display{
  display: contents;
}
.heart:hover{
  fill: white;
  stroke: red;
  cursor: pointer;
  transform: scale(1.2);
}
.jover{
  transition: transform 0.3s ease;

}
.jover:hover{
  transform: scale(1.05);
  z-index: 10;
  cursor: pointer;

}



</style>