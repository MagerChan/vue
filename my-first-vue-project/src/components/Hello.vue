<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input v-model="newItem" @keyup.enter="addNew"/>
    <ul>
      <li v-for="item in items" v-bind:class="{finished:item.isfinished}" v-on:click="toggleFinished(item)">
        {{item.label}}
      </li>
    </ul>
    <p>child tells me :{{childwords}}</p>
    <conponent-a msgfromfather="you die!" v-on:child-tell-me-something="listentomyboy"></conponent-a>
  </div>
</template>

<script>
import Store from '../store.js'
import conponentA from './conponentA.vue'
export default {
  name: 'hello',
  data () {
    return {
      msg: 'this is todo list',
      items:Store.fetch(),
      newItem:'',
      childwords:''
    }
  },
  components:{
    conponentA,
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
    },
    listentomyboy:function(msg){
      this.childwords=msg
    }
  },
  watch:{
    items:{
      handler:function(items){
        Store.save(items)
      },
      deep:true
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
