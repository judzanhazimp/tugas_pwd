<template>
  <div>
     <user v-for="(user, index) in users">
     :firstName="user.firstname"
     :lastName="user.lastName"
     :key="index"></user>
  </div>
</template>

<script>
import User from "@/components/User"
export default {
  name: 'Comp2',
  components: {
      User
  },

  data () {
    return {
      msg: 'Welcome to Vue.Js',
      number: 1,
      users:[
        {
            'firstName' : 'kampang',
            'lastName' : 'h3h3'
        }
      ]
    }
  },
  methods: {
    addnumber() {
      this.number++
    }
  },
  mounted() {
    this.number = 200
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
</style>
