<template>
  <div class="indicatorContainer flex flex-row">
    <div class="flex">
      <div class="progress-bar"/>      
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

</style>
