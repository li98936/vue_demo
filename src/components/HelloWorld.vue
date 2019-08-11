<template>
  <div class="hello">
    {{this.test}}
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  mounted(){
    const timestamp1 = new Date().getTime()
    this.$axios.get('http://47.95.214.60:3509/api/test').then((response)=>{
      console.log(response.data)
      this.test = response.data
      console.log(111111, new Date().getTime() - timestamp1)
    }).catch((response)=>{
      console.log(response)
      this.test = response
    })
  },
  data () {
    return {
      test: []
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
