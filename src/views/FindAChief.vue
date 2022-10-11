<template>
    <HeaderView Userpp="DefaultUser.jpg" UserLN="abc" UserFN="abc"/>
    <div class="ChiefList">
      <h2>This is all the Chief corresponding to your demands:</h2>
      <div><chief-card-home-pages cp="DefaultUser.jpg" AvGrade="5" ChiefFN="e" ChiefLN="e" Description="wola jui bonne"></chief-card-home-pages>
  </div>
  <chief-card-home-pages cp="DefaultUser.jpg" AvGrade="5" ChiefFN="a" ChiefLN=" " Description="wola jui bonne"></chief-card-home-pages>
  <chief-card-home-pages cp="DefaultUser.jpg" AvGrade="5" ChiefFN="b" ChiefLN=" " Description="wola jui bonne"></chief-card-home-pages>
  <chief-card-home-pages cp="DefaultUser.jpg" AvGrade="5" ChiefFN="c" ChiefLN="b" Description="wola jui bonne"></chief-card-home-pages>
  <chief-card-home-pages cp="DefaultUser.jpg" AvGrade="5" ChiefFN="d" ChiefLN="a" Description="wola jui bonne"></chief-card-home-pages>
  
  </div>
    <FilterView></FilterView>
  </template>
  
  <script>
  import HeaderView from '@/components/HeaderView';
  import ChiefCardHomePages from '@/components/ChiefCardChief.vue'
  import FilterView from '@/components/FilterView.vue';
  export default {
    components:
    {
      HeaderView,
      ChiefCardHomePages,
      FilterView
  }
  }
  </script>
  
  <style>
    .ChiefList{
      text-align:center;
    }
  </style>