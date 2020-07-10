<template>
  <div id="app">
    <div v-for="q in data">{{q}}</div>
  </div>
</template>

<script>
import Indicator from './components/Indicator.vue'
import Data from './arabicData.json'


export default {
  name: 'app',
  data () {
    return {
      data: []
    }
  },
 methods:{
    init(){
      this.data.push('jhg');
      this.data = Data;
      console.log(this.data);
    }
  },
  mounted(){
    this.init()
  }
}



</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
