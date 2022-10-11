<template>
    <nav>

<router-link to="/home"><div class="border">Home</div></router-link>
<router-link to="/chief"><div class="border">Find A Chief</div></router-link>
<router-link to="/"><div class="border">Disconnect</div></router-link>
</nav>
<router-view/>
    <div class="alignment">
  <img alt="Site logo" class="slogo" src="@/assets/logo.png">
  <h1>Chief4U</h1>
  <span class="righter"><img alt="User profile picture" :src="require(`@/assets/${Userpp}`)" id="userpp" @click="profil"><span id="usern"> {{UserFN}} {{UserLN}}</span></span>
  </div>
</template>

<script>
export default {
    name:"HeaderView",
    props:{
        Userpp:String,
        UserFN:String,
        UserLN:String
    },
    methods:{
        profil(){
            console.log()
            window.location.href = 'http://10.180.126.56:8080/?#/userprofil';
        }
    }
    }
</script>

<style>
    .alignment{
    display:flex;
    position:absolute;
    top:0px;
    margin:5px;

    }
    .slogo{
        width:55px;
        height:55px;
    }

  .righter{
    position:absolute;
    right:-1200px;
  }
  #userpp{
    border-radius: 50%;
    height:5vw;
    width:auto;
    border:1px solid black;
  }
  #usern{
    display:flex;
    position:absolute;
    top:30px;
    right:-70px;
    font-size:15px;
    font-style:oblique;
  }
</style>