<template>
   <div class="searchBx mt-4">
      <input v-model="val" @change="onChange" class="border-none rounded-bl-3xl rounded-tr-3xl outline-none shadow- p-4 w-full opacity-50 hover:opacity-100 hover:rounded-bl-sm hover:rounded-tr-sm hover:rounded-tl-3xl hover:rounded-br-3xl" type="text" placeholder="Search"/>
    </div>
  </template>

<script>
  export default{
    name:"SearchBox",
    data(){
      return{
        val:""
      }
    },
    methods:{
      onChange(){
        this.$emit("change-weather-val",this.val);        
      }
    }
  }

 </script>

<style scoped>
  .searchBx input{
    transition:0.2s;
   }
 
  </style>
