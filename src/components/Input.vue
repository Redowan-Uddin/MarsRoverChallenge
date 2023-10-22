<template>
  <div>    
    <div class="input-container">  
        <label>X-axis</label>
      <b-form-input v-model="xvalue" :type="type"></b-form-input>
    </div>
    <div class="input-container">
        <label>Y-axis</label>
      <b-form-input v-model="yvalue" :type="type"></b-form-input>
    </div>
    <div>
      <b-button :variant="color" @click="pushValues">Push</b-button>
      <div v-if='sent' class="fade-out">
        Info is sent and published
      </div>
        </div>
            <div v-if='largeNum' class="warning">
        Too large Number, reduce it to at least 100
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      sent: false,
      largeNum:false,
      type: 'number',
      color: 'outline-danger',
      xvalue: null,
      yvalue: null,
      x : null,
      y : null
    }
  },
    methods: {
    pushValues() {
        const x = parseFloat(this.xvalue);
        const y = parseFloat(this.yvalue);
        const maxLimit = 100;

        if (isNaN(x) || isNaN(y) || x > maxLimit || y > maxLimit) {
            this.largeNum = true;
            return;
        }
        this.largeNum = false;

        this.$emit('values', { x, y });

        this.x = x;
        this.y = y;

        this.xvalue = "";
        this.yvalue = "";

        this.sent = true;
        this.color = 'success';
        setTimeout(() => {
            this.color = 'outline-danger';
            this.sent = false
        }, 3000);
    },
  },
}
</script>

<style scoped>
.input-container {
  min-width: 50px;
}
.fade-out {
  opacity: 0.5 ;
  transition: opacity 1s;
  color: rgb(9, 80, 17);
}
.warning {
    opacity: 0.7 ;
    color: red;
}
</style>