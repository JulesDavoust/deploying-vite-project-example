<template>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css"
    rel="stylesheet"
    integrity="sha384-gH2yIJqKdNHPEq0n4Mqa/HGKIhSkIHeL5AyhkYV8i59U5AR6csBvApHHNl/vI1Bx"
    crossorigin="anonymous">
    <div class="container">
        <div class="row">
            <div class="col border">
                <img class="logoRegister" src="@/pictures/logoLogin.png" alt="logo login">
                <div id="textRegister">Registeration (chief)</div>
                <form id="form">
                    <div id="allRegister">
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
                            <select class="select" name="format" id="format" v-model="typeOfFood">
                                <option selected disabled>Type of food</option>
                                <option value="Italian">Italian</option>
                                <option value="African">African</option>
                                <option value="Greek">Greek</option>
                                <option value="Mediterranean">Mediterranean</option>
                                <option value="Portugese">Portugese</option>
                                <option value="Thai">Thai</option>
                                <option value="Spanich">Spanich</option>
                                <option value="Oriental">Oriental</option>
                                <option value="German">German</option>
                                <option value="French">French</option>
                                <option value="Indian">Indian</option>
                                <option value="Others">Others</option>
                            </select>
                        </div>
                        <div class="input">
                            <input type="text" placeholder="Password" v-model="password">
                        </div>
                        <div class="input">
                            <input type="text" placeholder="Verif Password" v-model="passwordVerif">
                        </div>
                    </div>
                    <button type="submit" id="button" @click.prevent="registerChiefFunction">Register</button><br>
                </form>
            </div>
        </div>
    </div>
</template>


<script>
import global from "../global.js"
import axios from 'axios';
export default {
    name:'registerationChiefComponent',
    data(){
        return{
            firstName:'',
            lastName:'',
            adress:'',
            phoneNumber:'',
            email:'',
            typeOfFood:'',
            password:'',
            passwordVerif:''
        }
    },
    methods:{
        registerChief(){
            axios.post('http://localhost:5000/chiefs', {
                firstName: this.firstName, lastName : this.lastName, adress: this.adress,
                phoneNumber: this.phoneNumber, email:this.email, typeOfFood:this.typeOfFood, password:this.password, passwordVerif:this.passwordVerif,}
            );
        },
        registerChiefFunction(){
            var ListOfChiefs = [];
            axios.get('http://localhost:5000/chiefs')
            .then((response) =>{
            var Chief = response.data;
            var verif = 0;
            ListOfChiefs = Chief;
            for(var i = 0; i<ListOfChiefs.length; i++){
                if(this.email == ListOfChiefs[i].email){
                    alert("Email already use");
                    verif = 1;
                }
            }
            if(verif == 0){
                this.registerChief();
                global.state.emailGlobal = this.email;  
                window.location.href = 'http://10.180.126.56:8080/?#/chiefprofil';
            }
            })
            .catch(error => {
            console.log(error);
            })
        }
    }
}
</script>

<style>
    #allRegister{
        width:20%;
        border:2px solid black;
        margin-left:40%;
        padding-top:1%;
        padding-bottom:1%;
    }


    .input{
        padding-top:4%;
    }


    #register{
        padding-top:1%;
    }
    #button{
        margin-top:1%;
        width: 20%;
    }
    .logoRegister{
        margin-right: 14%;
        padding-top:4%;
        width:4%;
    }
    #textRegister{
        margin-top:-2.9%;
        margin-left:3.8%;
    }

    .select{
        width:93%;
    }
</style>