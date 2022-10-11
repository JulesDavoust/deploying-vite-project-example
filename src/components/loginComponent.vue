<template>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css"
    rel="stylesheet"
    integrity="sha384-gH2yIJqKdNHPEq0n4Mqa/HGKIhSkIHeL5AyhkYV8i59U5AR6csBvApHHNl/vI1Bx"
    crossorigin="anonymous">
    <div class="container">
        <div class="row">
            <div class="col border">
                <img class="logoLogin" src="@/pictures/logoLogin.png" alt="logo login">
                <div id="textLogIn">Login</div>
                <form id="form">
                    <div id="all">
                        <div id="email">
                            <input type="text" placeholder="Email" v-model="email">
                        </div>
                        <div id="password">
                            <input type="text" placeholder="Password" v-model="password">
                        </div>
                    </div>
                    <button type="submit" id="login" @click.prevent="chiefOrNot">Log in</button><br>
                    <div id="register"><a href="http://10.180.126.56:8080/?#/register">Register</a></div> 
                </form>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import global from "../global.js"
export default {
    name:'loginComponent',
    data(){
        return{
            email:'',
            password:''
        }
    },
    methods:{
        loginFunction(){
            var ListOfUsers = [];
            axios.get('http://localhost:5000/users')
            .then((response) =>{
            var User = response.data;
            var verif = 0;
            ListOfUsers = User;
            for(var i = 0; i<ListOfUsers.length; i++){
                if(this.email == ListOfUsers[i].email && this.password == ListOfUsers[i].password){
                    global.state.emailGlobal = this.email;
                    verif = 1;
                }
            }
            if(verif == 1){
                window.location.href = 'http://10.180.126.56:8080/?#/home';
            }
            console.log(global.state.emailGlobal)
            })
            .catch(error => {
            console.log(error);
            })
        },
        loginChiefFunction(){
            var ListOfChiefs = [];
            axios.get('http://localhost:5000/chiefs')
            .then((response) =>{
            var Chief = response.data;
            var verif = 0;
            ListOfChiefs = Chief;
            for(var i = 0; i<ListOfChiefs.length; i++){
                if(this.email == ListOfChiefs[i].email && this.password == ListOfChiefs[i].password){
                    global.state.emailGlobal = this.email;
                    verif = 1;
                }
            }
            console.log(global.state.emailGlobal);
            if(verif == 1){
                window.location.href = 'http://10.180.126.56:8080/?#/chiefprofil';
            }
            console.log(global.state.emailGlobal)
            })
            .catch(error => {
            console.log(error);
            })
        },
        chiefOrNot(){
            console.log(global.state.ChiefOrNot);

            if(global.state.ChiefOrNot == "Oui"){
                console.log("chief");
                this.loginChiefFunction();
            }
            else{
                console.log("user");
                this.loginFunction();
            }
            
            
        },
    }

}
</script>

<style>
    #all{
        width:20%;
        border:2px solid black;
        margin-left:40%;
        padding-top:1%;
        padding-bottom:1%;
    }

    #form{
        margin-top:1.5%;
    }

    #password{
        padding-top:4%;
    }


    #register{
        padding-top:1%;
    }
    #login{
        margin-top:1%;
        width: 20%;
    }
    .logoLogin{
        margin-right: 7%;
        padding-top:4%;
        width:4%;
    }
    #textLogIn{
        margin-top:-2.9%;
        margin-left:3%;
    }
</style>