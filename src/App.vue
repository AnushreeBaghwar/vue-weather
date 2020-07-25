<template>
  <div id="app">
     New York,USA <br>
    wednesday 1 april
    <h1>26°</h1>
    Rain
    <input type="search" name="" id="search-bar" placeholder="Search...">
   
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return {
      api_key:'becd0525a5b19e7ed8384f10c3169c9c'
    }
  }

}

</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body{
background-image:url('./assets/weather2.jpg');
background-size: cover;
background-position: bottom;

}
input#search-bar {
    
    padding:10px;
    border-radius:20px;
    border-style:none;
    width:50%;
    outline:none;
    box-shadow:1px 2px 2px #3e3636;
    position:relative;
    top:50px;
    left:25%;
}

</style>
