<template>

  <div id="app">
  <h1 id="heading">Live Weather</h1>
     <form @submit.prevent=fetchData()>
     <div class="search-place"><input v-model="zip" type="tel" name="" id="search-bar" placeholder="Enter your Pin code.."></div></form>
   
   <div class="place_name">{{weather.name}}</div>
   <div class="date">{{weather.date}}</div>
   <div class="temperature">{{weather.temp}}°F</div>
   <div class="climate">{{weather.climate}}</div>

  
  </div>
</template>

<script>

import axios from 'axios'
export default {
  name: 'App',
  data(){
    return {
      api_key:'becd0525a5b19e7ed8384f10c3169c9c',
      zip:null,
      url : 'https://api.openweathermap.org/data/2.5/weather?',
      // +'zip=736205'+',IN&appid=',
      weather:{
        name:null,
        date:null,
        temp:null,
        climate:null,
        desc:null
      }
   }
    
  },
  created() {
    this.fetchData()
    },
    methods: {
      
      fetchData()

      {axios.get(this.url+'zip='+this.zip+',IN&appid='+this.api_key).then(res=>{
        console.log(res.data);
      
      this.weather.name=res.data.name;
      this.weather.temp=res.data.main.temp;
      this.weather.climate=res.data.weather[0].main;
      var d=((res.data.dt)*1000);
       this.weather.date=new Date(d);     
      });
      
        
      }
    },


}

</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body{
background-image:url('./assets/bg.jpg');
background-repeat: no-repeat;

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
.place_name {
    text-align:center;
    position:relative;
    top:100px;
    font-size:30px;
    font-family:cursive;

}
.date {
    position:relative;
    text-align:center;
    top:120px;
    font-size:20px;
    
}
.temperature {
    position:relative;
    text-align:center;
    top:150px;
    font-weight:bold;
    font-family:cursive;
font-size:50px;
      color: bisque;
}
.climate {
    text-align:center;
    position:relative;
    top:160px;
    font-family:cursive;
    font-size:30px;

}
.date {
    font-family:cursive;
    font-size:15px;
}
#heading{
  font-family: cursive;
  text-align:center;
  font-size:20px;
position:relative;
top:20px;
}
</style>
