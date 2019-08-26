<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png" />
        <div>
            <form @submit="registerClicked">
                <div>
                    <input type="email" v-model="email" placeholder="Email" />
                </div>
                <div>
                    <input type="password" v-model="password" placeholder="Password" />
                </div>
                <div>
                    <button type="submit">Register</button>
                </div>
            </form>
        </div>
  </div>
</template>

<script>
// @ is an alias to /src
import firebase from 'firebase';
import router from "../router";
export default {
    name: "register",
    data: function(){
        return{
            email: '',
            password: '',
        }
    },
    methods:{  
        registerClicked: function(e){
            e.preventDefault();
            firebase.auth().createUserWithEmailAndPassword(this.email, this.password).then(
                function(user){
                    alert("Account has been created");
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
