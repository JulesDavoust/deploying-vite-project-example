<template>
    <article class="ChiefCardHomePages">
      <div class="Cdec">
      <img alt="Chief Picture" :src="require(`../assets/${cp}`)" class="Chiefp">
      <div class="a">
      <h2 class="cn">{{ChiefFN}} {{ChiefLN}}</h2>
  
      <div class="grade"><img src="../assets/heart.png" alt="grade logo" class="HeartOne"> {{AvGrade}}</div>
  
      <div class="Desc">{{Description}}
  
      <span class="buttonClass">
      <button class="Learnmore" @click=chiefprofile()>Get information</button>
      </span>
      </div>
      </div>
      </div>
    </article>
  </template>
  
  <script>
  export default {
      props:{
          cp:String,
          ChiefFN:String,
          ChiefLN:String,
          AvGrade:String,
          Description:String,
      },
      methods:{
          chiefprofile : function(){
              this.$router.push('/');
          }
      }
  }
  </script>
  
  <style>
      .a{
         display:block; 
         padding:20px;
      }
  
      .Cdec{
          border:1px solid black;
          background-color: blanchedalmond;
          height:200px;
          font-size:18px;
          margin-left:275px;
          padding:2px;
          display:inline-flex;
          width:80vw;
          text-align:left;
      }
      .Chiefp{
          margin-left:10px;
          border-radius: 50%;
          border:1px solid black;
      }
      .HeartOne{
          width:20px;
          height:20px;
      }
      .grade{
          display:flex;
  }
      .cn{
          margin-block:10px;
      }
      .Desc{
          font-size:10px;
      }
      .Learnmore{
  
              border:none;
              background:rgba(255, 210, 143, 0.874);
              border:none;
              border-radius: 10px;
      }
      .Learnmore:hover{
          color:orange;
      }
  </style>