<template>

<div id="app">
  {{ info }}
</div>



</template>


<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return {
      info: null
    }
  },
  
  mounted () {
    axios
      .get('https://api.github.com/users/RomainWia/repos')
      .then(response => {
        this.info = response.data
      })
      .catch(error => {
        console.log(error)
        this.errored = true
      })
      .finally(() => this.loading = false)
  }    
  
}
</script>



<style scoped>

</style>
