<template>
  <div class="container">
    <div class="image-container">
      <Map />
    </div>
    <div>
      <Pointer :x="x" :y="y" />
    </div>
    <div class="input-container">
      <Input @values="updateValues" />
    </div>
  </div>
</template>

<script>
import Map from './components/Map.vue'
import Input from './components/Input.vue'
import Pointer from './components/Pointer.vue'

export default {
  components: {
    Map,
    Input,
    Pointer
  },
  
  data() {
       return {
          x: null,
          y: null,
       };
     },
       methods: {
        updateValues({ x, y }) {
          this.x = x;
          this.y = y;
        },
  },
     
}
</script>

<style scoped>
  .container {
    border: 3px solid black;
    width: 100%;
    display: flex;
    justify-content: space-between;
  }
   .image-container {
    text-align: left;
    margin-right: auto;
   }
   .input-container {
    text-align: left;
    margin-left: auto;
}

</style>>