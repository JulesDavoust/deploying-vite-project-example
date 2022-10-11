<template>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css"
    rel="stylesheet"
    integrity="sha384-gH2yIJqKdNHPEq0n4Mqa/HGKIhSkIHeL5AyhkYV8i59U5AR6csBvApHHNl/vI1Bx"
    crossorigin="anonymous">
    <div><img class="profilLogin" src="@/pictures/profilPicture.png"><div class="profilNameLogin">{{firstName}}</div></div>
    <div class="nameSiteProfil"><a style="text-decoration: none; color:black" href="#">Chief4U</a></div>
    <div class="container">
        <div class="row">
            <div class="col col1">
                <form>
                    <img class="profilPicture" src="@/pictures/profilPicture.png">
                    <div class="FLName">{{firstName}} {{lastName}}</div>
                    <div class="grade">{{grade}} Average grade</div>
                    <div class="infos">
                        <div>Informations :</div>
                        <div class="styleInfos">
                            <div></div>Email :&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;&ensp;Phone Number :
                            <br><input type="text" placeholder="Email" v-model="email">
                            <input class="phoneNumberProfil" type="text" placeholder="Phone number" v-model="phoneNumber"><br>
                            <div  class="passwordProfil">Password :<br> <input type="text" placeholder="Phone number" v-model="password"></div>
                            <div class="typeOfFoodProfil">Type of Food : 
                            <select class="select" name="format" id="format" v-model="typeOfFood">
                                        <option selected disabled>{{typeOfFood}}</option>
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
                                    </select><br></div>
                        </div>
                    </div>
                    <button type="submit" class="sInfo" @click.prevent="printInfoChief">Save</button>
                </form>
            </div>
            <div class="col col2">
                <form>
                    <div class="description">
                        <div class="textDesc">Description :</div>
                        
                    </div>
                    <textarea class="areaDesc" v-model="description"></textarea>
                </form>
            </div> 
        </div>   
    </div>
</template>

<script>
import axios from 'axios';
import global from "../global.js"
export default {
    name:'chiefProfilComponent',
    data(){
        return{
            picture:'',
            grade:'4.6',
            profilPicture:'',
            firstName:'',
            lastName:'',
            email:'',
            typeOfFood:'',
            phoneNumber:'',
            description:'',
            password:''

        }
    },
    beforeMount(){
                    axios.get('http://localhost:5000/chiefs/'+global.state.emailGlobal)
                    .then((response) =>{
                    var Chief = response.data;
                    var ListOfChief = [];
                    ListOfChief = Chief;
                    this.firstName = ListOfChief.firstName;
                    this.lastName = ListOfChief.lastName;
                    this.email = ListOfChief.email;
                    this.phoneNumber = ListOfChief.phoneNumber;
                    this.typeOfFood = ListOfChief.typeOfFood;
                    this.password = ListOfChief.password;
                    this.description = ListOfChief.description;
                    console.log(this.typeOfFood)
                    })
                    .catch(error => {
                    console.log(error);
                    })
            
        },
    methods:{
        printInfoChief(){
            axios.patch('http://localhost:5000/chiefs/'+global.state.emailGlobal, {
                phoneNumber: this.phoneNumber, email: this.email, password: this.password, description : this.description, typeOfFood : this.typeOfFood
            });
        }
        
    }

}
</script>

<style>
    

    .profilPicture{
        border-radius: 90%;
        width:35%;
        margin-top:10%;
        margin-right:80%;
    }

    .nameSiteProfil{
        margin-top:-3.5%;
        margin-right:84%;
        font-size:40px;
    }

    .profilLogin{
        border-radius: 90%;
        margin-left:60%;
        margin-top:3.5%;
        width:5%;
    }
    .profilNameLogin{
        margin-top:-3.5%;
        margin-left:70%;
    }

    .FLName{
        margin-top:-25%;
        margin-right:-32%;
        font-size: 50px;
    }

    .grade{
        font-size:20px;
        margin-right:-5%;
    }

    .styleInfos{
        width:90%;
        border:2px solid black;
        padding-left:2%;
        margin-top:2%;
        
        
    }

    .infos{
        text-align: left;
        margin-left: 8%;
        margin-top:14.8%;
    }

    .phoneNumberProfil{
        margin-left: 2%;
    }

    .passwordProfil{
        margin-top:2%;
    }

    .typeOfFoodProfil{
        margin-top:2%;
        width:50%;
    }


    .areaDesc{
        width:100%;
        min-height: 180px;
        max-height: 180px;
        margin-top:1.6%;
    }

    .textDesc{
        text-align: left;
    }

    .description{
        margin-top:55.6%;

    }

    .sInfo{
        margin-top:1%;
        margin-left:-58%;
        width:26%;
        border:2px solid black;
    }

    .sDesc{
        width: 27%;
        margin-right: 75.5%;
    }

</style>