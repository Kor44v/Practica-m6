<template>
  <div>
    <GameComp :id='id'></GameComp>
  </div>
</template>

<script>
  import GameComp from "@/components/GameComp.vue";
  
export default {
  name: "game-view",
  created() {},
  data() {
    return {};
  },
  props: {
    id:{
      type:String,
      required:true
    }
  },
  methods: {},
  components:{
    GameComp
  }
};
</script>

<style lang="scss" scoped></style>