<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <div>
        Hello {{user.email}}
    </div>
    <div>
        <button @click="logoutClicked">Logout</button>
    </div>
  </div>
</template>

<script>
import firebase from "firebase";
import router from '../router';
export default {
    name: "welcome",
    data: function(){
        return{
            user: {},
        }
    },
    methods:{
        logoutClicked: function(){
            firebase.auth().signOut().then(function(){
                router.push('/');
            }).catch(function(error){
                alert(error.message);
            });
            
        }
    },
    mounted(){
        this.user = firebase.auth().currentUser;
    }
};
</script>
