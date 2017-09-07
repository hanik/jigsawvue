<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li>
        <div class="button test" @click="call">call to server</div>
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
        let element = this.$el.querySelector('.test')
        if (element.classList.contains('on')) {
          element.classList.remove('on')
          this.$data.testData = 'testData'
        } else {
          element.classList.add('on')
          let baseURI = process.env.API_URL
          this.$http.get(`${baseURI}/test`)
            .then((result) => {
              console.log(result)
              this.$data.testData = result.data
            })
        }
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
    background-color: aliceblue;
    cursor: pointer;
    border: 1px solid lightgray;
    font-size: 16px;
    padding: 10px;
  }
  .test {
    background-color: azure;
  }

  .on {
    background-color: lightskyblue;
  }
</style>
