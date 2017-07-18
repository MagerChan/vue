<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1 v-text="msg"></h1>
    <h1 v-html="msg"></h1>
    <ul>
      <li v-for="item in items" v-bind:class="{finished:item.isfinished}">
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
      items:[
        {
          label:'coding',
          isfinished:false
        },
        {
          label:'walking',
          isfinished:true
        }
      ]
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

.finished{
  text-decoration:underline;
}
</style>
