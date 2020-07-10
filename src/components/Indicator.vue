<template>
  <div class="flex flex-row">
    <div class="flex flex-1 flex-column">
      <div class="flex flex-row space-arround">
       <img v-for="item in maxSteps" :src="'../../src/assets/emptyemoji.png'" class="img-small">
      </div>
      <div class="progress-bar">
        <div class="up-arrow" v-bind:style="{'left' : position+'px'}">
        </div>
      </div>      
    </div>
  </div>
</template>

<script>
export default {
  name: 'Indicator',
  data () {
    return {
      position: this.maxSteps * 77.2,
    }
  },
  props: {
  	maxSteps: {
      type: Number,
      default: 10,
  	},
  	step: {
      type: Number,
      required: true,
  	},
  },
  watch: { 
    step: function(newVal, oldVal) { 
      if(newVal != oldVal){
        this.position -= 82; 
      };
    },
  },
  methods:{
   
  },
  mounted() {
    console.log(this.maxSteps,'llllllllllllllllllllllllllll')
  }
}
</script>

<style>
.progress-bar {
  width: 100%;
  height: 5px;
  background-color: orange;
  position: relative;
  margin-top: 10px;
}
.flex-1 {
  flex: 1;
}
 .up-arrow {
  position: absolute;
  width: 0; 
  height: 0; 
  border-left: 10px solid transparent;
  border-right: 10px solid transparent;
  border-bottom: 10px solid orange;
  transition: 0.5s left ease-out;
  bottom: 5px;
 }
.img-small {
  max-height: 60px !important;
  width: auto;
  padding: 10px
}
.space-arround {
  justify-content: space-between;
}
</style>
