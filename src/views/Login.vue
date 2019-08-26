<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png" />
        <div>
            <form @submit="loginClicked">
                <div>
                    <input type="email" v-model="email" placeholder="Email" />
                </div>
                <div>
                    <input type="password" v-model="password" placeholder="Password" />
                </div>
                <div>
                    <button type="submit">Login</button>
                </div>
            </form>
        </div>
  </div>
</template>

<script>
// @ is an alias to /src
import firebase from "firebase";
import router from '../router';
export default {
    name: "login",
    data: function(){
        return{
            email: '',
            password: '',
        }
    },
    methods:{  
        loginClicked: function(e){
            e.preventDefault();
            firebase.auth().signInWithEmailAndPassword(this.email, this.password).then(
                function(user){
                    alert("Successfully Logged In!");
                    router.push('welcome');
                },
                function(err){
                    alert(err.message);
                }
            )
        }
    }
};
</script>
