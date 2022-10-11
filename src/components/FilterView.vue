<template>
    <article class="block">
  <ul class="filter">
        <li v-for="filter in filters" :key="filter.filtern" class="filterl">
            <!-- Need to add the check to do the filter -->

            {{filter.filtern}}
        </li>
    </ul>

    </article>
</template>

<script>
export default {
    data() {
        return {
            filters: [
            { id:"1" , filtern :'Italian'},
            { id:"2" , filtern :'Russian'},
            { id:"3" , filtern :'French'},
            { id:"4" , filtern :'Japanese'},
            { id:"5" , filtern :'Chinese'}

        ]
    }
    }
}
</script>

<style>
    .filter{
        display:fixed;
    }
    .block{
        border:2px solid black;
  position: fixed;
  bottom: 10px;
  left: -2px;
  width: 200px;
  height:587px;
  border: 3px solid #000000;
    }
    .filterl{
        margin-left:10px;
        margin-top:3px;
        display:inline-block;
    }
</style> 
