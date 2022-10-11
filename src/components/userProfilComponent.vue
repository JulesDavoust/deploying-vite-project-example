<template>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css"
    rel="stylesheet"
    integrity="sha384-gH2yIJqKdNHPEq0n4Mqa/HGKIhSkIHeL5AyhkYV8i59U5AR6csBvApHHNl/vI1Bx"
    crossorigin="anonymous">
    <div><img class="profilLogin" src="@/pictures/profilPicture.png"><div class="profilNameLogin">{{firstName}}</div></div>
    <div class="nameSiteProfil"><a style="text-decoration: none; color:black" href="http://10.180.126.56:8080/?#/home">Chief4U</a></div>
    
    <div class="container">
        <div class="row">
            <div class="col col1">
                <form >
                    <img class="profilUserPicture" src="@/pictures/profilPicture.png">
                    <div class="FLNameUser">{{firstName}} {{lastName}}</div>
                    <div class="infosUser">
                        <div>Informations :</div>
                        <div class="styleInfosUser">
                            <div></div>Email :&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;&ensp;Phone Number :
                            <br><input type="text" placeholder="Email" v-model="email">
                            <input class="phoneNumberUserProfil" type="text" placeholder="Phone number" v-model="phoneNumber"><br>
                            <div  class="passwordUserProfil">Password :<br> <input type="text" placeholder="Phone number" v-model="password"></div>
                        </div>
                    </div>
                    <button type="submit" class="sInfoUser" @click.prevent="printInfo">Save informations</button>
                </form>
            </div>
        </div>   
    </div>
</template>

<script>
import axios from 'axios';
import global from "../global.js"
export default {
    name:'userProfilComponent',
    data(){
        return{
            picture:'',
            profilPicture:'',
            firstName:'',
            lastName:'',
            email:'',
            phoneNumber:'',
            password:''
        }
    },
    created(){

                    console.log('boucle else')
                    console.log(global.state.emailGlobal)
                    axios.get('http://localhost:5000/users/'+global.state.emailGlobal)
                    .then((response) =>{
                    var User = response.data;
                    var ListOfUser = [];
                    ListOfUser = User;
                    this.firstName = ListOfUser.firstName;
                    this.lastName = ListOfUser.lastName;
                    this.email = ListOfUser.email;
                    this.phoneNumber = ListOfUser.phoneNumber;
                    this.password = ListOfUser.password;
                    })
                    .catch(error => {
                    console.log(error);
                    })
                    
            
        },
    methods:{
        printInfo(){
            axios.patch('http://localhost:5000/users/'+global.state.emailGlobal, {
                phoneNumber: this.phoneNumber, email: this.email, password: this.password, 
            });
        }
        
    }
}
</script>

<style lang="scss">
    .profilUserPicture{
        border-radius: 90%;
        width:17%;
        margin-top:5%;
        margin-right:30%;
    }

    .FLNameUser{
        margin-top:-12.5%;
        margin-right:-20%;
        font-size: 50px;
    }


    .styleInfosUser{
        width:60%;
        border:2px solid black;
        padding-left:2%;
        margin-top:2%;
        
        
    }

    .infosUser{
        text-align: left;
        margin-left:33%;
        margin-top:9%;
    }

    .phoneNumberUserProfil{
        margin-left: 2%;
    }

    .passwordUserProfil{
        margin-top:2%;
        margin-bottom: 2%;
    }

    .sInfoUser{
        margin-top:1%;
        margin-left:-21%;
        border:2px solid black;
    }

</style>