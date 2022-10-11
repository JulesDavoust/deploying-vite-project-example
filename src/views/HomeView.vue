<template>
  <HeaderView Userpp="DefaultUser.jpg" UserLN="abc" UserFN="abc"/>
<div class="home">
  <HelloWorld class="underlined" msg="Welcome to Chief4U"/>
  <br/>
  <br/>
  <h3><p id="WebsiteD">
  Our website has been created for people who wants to feel luxury and discover more about traditional chief's food.<br/>
  Chiefs and non-chiefs are here to have a wonderful time having a good time eating different food from usual.<br/>
  We will provide the necessary information for you to find the perfect match !<br/>
  <br/>
  <br/>

  <br/>
  </p></h3>
  <container>
  <chief-card-home-page cp="logo.png" AvGrade="5" ChiefFN="a" ChiefLN=" " Description="wola jui bonne nostri pedites ad eos persequendos scandere clivos sublimes etiam si lapsantibus plantis fruticeta prensando vel dumos ad vertices venerint summos, inter arta tamen et invia nullas acies explicare permissi nec firmare nisu valido gressus: hoste discursatore rupium abscisa volvente, ruinis ponderum inmanium cper prona discedunt."></chief-card-home-page>
  <chief-card-home-page cp="logo.png" AvGrade="5" ChiefFN="test" ChiefLN=" " Description="wola jui bonne"></chief-card-home-page>
  <chief-card-home-page cp="logo.png" AvGrade="5" ChiefFN="test" ChiefLN="abc" Description="wola jui bonne"></chief-card-home-page>

</container>
</div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import ChiefCardHomePage from '@/components/ChiefCardHome.vue'
import HeaderView from '@/components/HeaderView.vue'

export default {
name: 'HomeView',
components: {
  HelloWorld,
  ChiefCardHomePage,
  HeaderView,
}
}
</script>

<style>
container{
  display:flex;
}
.home{
  margin-left:10%;
}
</style>