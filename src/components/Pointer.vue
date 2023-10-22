<template>
    <div :style="pointerStyle" class="pointer" >
        <img :src="pointerUrl" alt="pointer"/> {{x_axis}} {{y_axis}}
    </div>
</template>

<script>
export default {
  props: {
    x: {
        type: Number,
        required: true,
    },
    y: {
        type: Number,
        required: true,
    },
  },
  data() {
       return {
         pointerUrl: require('@/assets/Pointer.png'),
         x0 : 120,
         y0 : 2,
         x_axis: 0,
         y_axis: 0,
         maths: true,
       };
     },
    mounted() {
        this.startMaths();
  },
    watch: {
        x(newValue) {
            this.startMaths(newValue, this.y);
        },
        y(newValue) {
            this.startMaths(this.x, newValue);
        },
  },
    methods: {
        startMaths() {
            const x = this.x;
            const y = this.y;

            this.x_axis = (x / 100) * 700 + this.x0;
            this.y_axis = (y / 100) * 700 + this.y0;
        },
    },
   computed: {
    pointerStyle() {
      return {
        position: 'absolute',
        left: this.x_axis + 'px',
        top: this.y_axis + 'px',
      };
    },
  }
}
</script>

<style scoped>
.pointer{
  transition: transform 0.3s ease-in-out;
}
.pointer:hover{
  transform: scale(5);
}
</style>>