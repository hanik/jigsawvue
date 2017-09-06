<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li>
        <div class="button" @click="call">call to server</div>
      </li>
      <li>{{testData}}</li>
    </ul>
  </div>
</template>

<script>
  import axois from 'axios'

  export default {
    name: 'hello',
    data () {
      return {
        msg: 'Welcome to Your Vue.js App',
        testData: 'testData'
      }
    },
    methods: {
      call: function () {
        this.$data.testData = 'call to server button clicked!'
        axois.get(process.env.API_URL + '/test')
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
  .button {
    height: 24px;
    background-color: antiquewhite;
    cursor: pointer;
    border: 1px solid lightgray;
    font-size: 16px;
    padding: 10px;
  }
</style>
