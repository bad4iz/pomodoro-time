<template>
  <v-container fluid>
    <v-slide-y-transition mode="out-in">
      <v-layout column align-center>
       <div class="circle">
         <div class="str"></div>
       </div>
      </v-layout>
    </v-slide-y-transition>
  </v-container>
</template>

<style>
  .circle{
    background-color: red;
    width: 500px;
    height: 500px;
    border-radius: 50%;
  }
  .srt{
    width: 12px;
    height: 100px;
    background-color: black;
    margin: auto;
  }
</style>
