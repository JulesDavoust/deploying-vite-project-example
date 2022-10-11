<template>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css"
    rel="stylesheet"
    integrity="sha384-gH2yIJqKdNHPEq0n4Mqa/HGKIhSkIHeL5AyhkYV8i59U5AR6csBvApHHNl/vI1Bx"
    crossorigin="anonymous">
    <div class="container">
        <div class="row">
            <div class="col border">
                <img class="logoRegister" src="@/pictures/logoLogin.png" alt="logo login">
                <div id="textRegister">Registeration (User)</div>
                <form id="form">
                    <div id="all">
                        <div class="input1">
                            <input type="text" placeholder="First name" v-model="firstName">
                        </div>
                        <div class="input">
                            <input type="text" placeholder="Last name" v-model="lastName">
                        </div>
                        <div class="input">
                            <input type="text" placeholder="Adress" v-model="adress">
                        </div>
                        <div class="input">
                            <input type="text" placeholder="Phone Number" v-model="phoneNumber">
                        </div>
                        <div class="input">
                            <input type="text" placeholder="Email" v-model="email">
                        </div>
                        <div class="input">
                            <input type="text" placeholder="Password" v-model="password">
                        </div>
                        <div class="input">
                            <input type="text" placeholder="Verif Password" v-model="passwordVerif">
                        </div>
                    </div>
                    <button type="submit" id="button" @click.prevent="registerFunction">Register</button><br>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
import global from "../global.js";
import axios from 'axios';
export default {
    name:'registerationUserComponent',
    data(){
        return{
            firstName:'',
            lastName:'',
            adress:'',
            phoneNumber:'',
            email:'',
            password:'',
            passwordVerif:''
        }
    },
    methods:{
        registerUser(){
            console.log('envoyé !')
            axios.post('http://localhost:5000/users', {
                firstName: this.firstName, lastName : this.lastName, adress: this.adress,
                phoneNumber: this.phoneNumber, email:this.email, password:this.password, passwordVerif:this.passwordVerif
            });
        },
        registerFunction(){
            var ListOfUsers = [];
            axios.get('http://localhost:5000/users')
            .then((response) =>{
            var User = response.data;
            var verif = 0;
            ListOfUsers = User;
            for(var i = 0; i<ListOfUsers.length; i++){
                if(this.email == ListOfUsers[i].email){
                    alert("Email already use");
                    verif = 1;
                }
            }
            if(verif == 0){
                this.registerUser();
                global.state.emailGlobal = this.email;
                window.location.href = 'http://10.180.126.56:8080/?#/home';
            }
            })
            .catch(error => {
            console.log(error);
            })
        }
    }
}
</script>