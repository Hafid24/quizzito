<template>
  <div class="indicatorContainer flex flex-column"/>
    <div class="flex">
      <div class="progress-bar"/>      
    </div>
  </div>
</template>

<script>
export default {
  name: 'indicator',
  data () {
    return {
      position: 0,
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
