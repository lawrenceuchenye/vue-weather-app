<template>
  <div>
     <SearchBox @change-weather-val="getWeather" />
     <LocationInfo v-if="!loading" :location="location" :date="getDate()" :temp="Math.round(temp)" :weather="weather"/>
   </div>
</template>

<script>
import SearchBox from "./components/SearchBox.vue";
import LocationInfo from "./components/LocationInfo.vue";

export default {
  name: 'App',
  components: {
   SearchBox,
   LocationInfo
  },
  data(){
    return {
       API_KEY:"cc8836ed22bfdc899377fdcc0b2666e8",
       URL_BASE:"https://api.openweathermap.org/data/2.5/",
       query:"",
       location:"",
       temp:"",
       weather:"",
       loading:true
    }
  },
  methods:{
   getWeather(val){
     this.query=val;
     this.loading=true;
     this.getResult()
   },
   getResult(){
      fetch(`${this.URL_BASE}weather?q=${this.query}&units=metric&APPID=${this.API_KEY}`).then(res=>{
        return res.json();
      }).then(json=>{
       this.temp=`${json.main.temp}`;
       this.location=`${this.query},${json.sys.country}`;
       this.weather=`${json.weather[0].main}`;
       this.loading=false;
      });
   },
   getDate(){
     let d=new Date();
     let months=["January","Feburary","March","April","May","June","July","August","September","October","November","December"];
     let days=["Sunday","Monday","Tuesday","Wenesday","Thursday","Friday","Saturday"];
  
     let day=days[d.getDay()];
     let date=d.getDate();
     let month=months[d.getMonth()];
     let year=d.getFullYear();

     return `${day} ${date} ${month},${year}`;
   }
  },
  created(){
    this.getWeather("Lagos");
    this.loading=false;
  }
}
</script>

<style>
 #app{
   background-image:linear-gradient(rgba(0,0,0,0.3),rgba(0,0,0,0.7)),url("./assets/cold-bg.jpg");
   background-size:cover;
   background-position:center;
   height:100vh;
   padding:10px;
 }

 *{
   margin:0;padding:0;
 }
</style>
