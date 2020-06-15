<template>
  <div class="home">
 
    <p> Bienvenido al Home</p>
     <button @click="quienSoy">Quien soy</button>
        <button @click="logOut">Salir</button>

  </div>
</template>

<script>
import Firebase from 'firebase'
export default {
  name: 'Home',

methods: {
logOut(){
      Firebase.auth().signOut().
      then(() => {
        this.$router.push({name:'Login'});

      })
    },

quienSoy(){
      let currentUser = Firebase.auth().currentUser
      console.log(currentUser) 
    },
    logOut(){
      Firebase.auth().signOut().
      then(() => {
        this.$router.push({name:'Login'});

      })
    }
}
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
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