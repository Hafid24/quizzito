<template>
  <div id="app" class="flex flex-column">
    <div>
    </div>
    <div>
    </div>
  </div>
</template>

<script>
import Indicator from './components/Indicator.vue'
import Quiz from './components/Quiz.vue'
import Data from './arabicData.json'


export default {
  name: 'app',
  components: {
    Indicator,
    Quiz
  },
  data () {
    return {
      data: []
    }
  },
 methods:{
    init(){
      this.data = Data;
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

.flex {
  display: flex
}
.flex-column  { 
  flex-direction: column 
}
.flex-row { 
  flex-direction: row 
}
</style>
