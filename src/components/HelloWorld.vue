<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button @click="hello">hello4</button>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',

  props: {
    msg: String
  },

  methods: {
    hello () {
      axios({
        method: 'post',
        url: 'https://i5a204.p.ssafy.io:5000/api/get-token',
        // headers: {'Content-type': 'application/json'},
        data: {"sessionName": "asd"}
      })
        .then(res => {
          console.log(res)
        })
        .catch(err => {
          console.warn(err);
        })
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
</style>
