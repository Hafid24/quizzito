<template>
  <div class="flex flex-row">
    <div class="flex flex-1 flex-column">
      <div class="flex flex-row space-arround">
       <img :src="'../../src/assets/emptyemoji.png'" class="img-small">
       <img :src="'../../src/assets/emptyemoji.png'" class="img-small">
       <img :src="'../../src/assets/emptyemoji.png'" class="img-small">
       <img :src="'../../src/assets/emptyemoji.png'" class="img-small">
       <img :src="'../../src/assets/emptyemoji.png'" class="img-small">
      </div>
      <div class="progress-bar">
        <div class="up-arrow">
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
      position: 0,
    }
  },
  props: {
    artists: {
      type: Number
    }
  },
  methods:{
    changePosition(){
       
    }
  },
}
</script>

<style>
.progress-bar {
  width: 100%;
  height: 5px;
  background-color: orange;
  position: relative;
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
  max-height: 40px !important;
  width: auto;
}
.space-arround {
  justify-content: space-between;
}
</style>
