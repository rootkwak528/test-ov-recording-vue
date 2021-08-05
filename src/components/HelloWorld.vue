<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button @click="hello">hello</button>
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
      this.httpRequest(
        'POST',
        'https://i5a204.p.ssafy.io:5000/api/get-token', {
          sessionName: 'hello from hogeun'
        },
        'Request of TOKEN gone WRONG:',
        res => {
          const token = res[0]; // Get token from response
          console.warn('Request of TOKEN gone WELL (TOKEN:' + token + ')');
        }
      );
    },

    httpRequest (method, url, body, errorMsg, callback) {
      axios({
        method,
        url,
        headers: {'Content-type': 'application/json'},
        data: body
      })
        .then(res => {
          callback(res)
          console.log(res)
        })
        .catch(err => {
          console.warn(errorMsg + ' (' + err.status + ')');
          console.warn(err.message);
        })
    }
  }
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
