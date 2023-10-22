<template>  
    <div>
     <img :src="imageUrl" alt="My Image" class="expanded-image"/>
    </div>
</template>

<script>
export default {
  data() {
       return {
         imageUrl: require('@/assets/image2.jpg'),
       };
     }
}
</script>

<style scoped>

</style>>