<template>
  <div class="hello">
    {{this.test}}
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  mounted(){
    let data = []
    const timestamp1 = new Date().getTime()
    this.$axios.get('http://47.95.214.60:8888/api/test1').then((response)=>{
      data.push(response.data)
      this.$axios.get('http://47.95.214.60:8888/api/test2').then((response)=>{
        data.push(response.data)
        this.$axios.get('http://47.95.214.60:8888/api/test3').then((response)=>{
          data.push(response.data)
          this.$axios.get('http://47.95.214.60:8888/api/test4').then((response)=>{
            data.push(response.data)
            this.test = data
            console.log(111111, new Date().getTime() - timestamp1)
          }).catch((response)=>{
            this.test = response
          })
        }).catch((response)=>{
          this.test = response
        })
      }).catch((response)=>{
        this.test = response
      })
    }).catch((response)=>{
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
