<template>
  <div class="Login">
 <p>Correo</p>
    <input type="text" v-model="email" />

    <p>Contraseña</p>
    <input type="text" v-model="password" />
    <button @click="login">Login</button>

  </div>
</template>
<script>
import Firebase from 'firebase'
export default {
  name:'Login',
  data() {
    return {
      email:'',
      password:''

    }
  },
  methods: {
    login(){
      Firebase.auth()
      .signInWithEmailAndPassword(this.email, this.password)
      .then(
        accept =>{
          alert('fuiste logeado, revisa la consola');
          this.quienSoy;
          this.$router.push({name:'Home'});
        },
        reject=>{
          alert('no estas registrado')
          console.log(reject.message);
        }
      )
    }, 

    quienSoy(){
      let currentUser = Firebase.auth().currentUser
      console.log(currentUser) 
    },
    logOut(){
      Firebase.auth().signOut();
    }
  },

}
</script>