<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1 v-text="msg"></h1>
    <h1 v-html="msg"></h1>
    <input v-model="newItem" @keyup.enter="addNew"/>
    <ul>
      <li v-for="item in items" v-bind:class="{finished:item.isfinished}" v-on:click="toggleFinished(item)">
        {{item.label}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: '<span>??</span>Welcome to todo list',
      items:[],
      newItem:''
    }
  },
  methods:{
    toggleFinished: function(item){
      item.isfinished = !item.isfinished
    },
    addNew:function(){
      this.items.push({
        label:this.newItem,
        isfinished:false
      })
      this.newItem=''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  padding: 0;
}

li {
  margin: 0 10px;
}

a {
  color: #42b983;
}

.finished{
  text-decoration:underline;
}
</style>
