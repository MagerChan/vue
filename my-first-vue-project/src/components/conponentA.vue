<template>
  <div class="hello">
    <h1>{{msg}}</h1>
    <button v-on:click="OnClickMe">Click</button>
  </div>
</template>

<script>
export default {
  data(){
    return{
      msg:'i love you'
    }
  },
  props:['msgfromfather'],
  methods:{
    OnClickMe:function(){
      this.$emit('child-tell-me-something',this.msg)
    }
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
</style>
