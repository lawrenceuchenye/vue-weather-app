<template>
   <div class="m-4 flex flex-col items-center justify-center ">
      <div class="">
         <h1 class="text-3xl font-bold text-white my-2 ml-14">{{location}}</h1>
         <h3 class="text-2xl font-light text-white">{{date}}</h3>
       </div>
    </div>
    <div class="flex justify-center mt-10">
     <div style="border-bottom:3px solid #fff;background:rgba(255,255,255,0.2);text-shadow:0 0 2px grey" class="border-b-gray-400 bg-gray-300 w-3/4 h-40 rounded flex flex-col justify-center  items-center">
        <h2 class="text-white text-4xl font-bold">{{temp}}°C</h2>
        <h4 class="text-white text-1xl font-bold">{{weather}}</h4>
      </div>
   </div>
  </template>

<script>
   export default{
     name:"LocationInfo",
     props:{
       location:String,
       date:String,
       temp:String,
       weather:String
     }
    }
  </script>

<style>
 </style>
