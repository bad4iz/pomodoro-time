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
<script>
  /* eslint-disable no-shadow */

  export default {
    data() {
      return {
        title: 'Vuetify.js',
      };
    },
    created() {

    },
    mounted() {
      const circle = document.querySelector('.circle');
      circle.ondragstart = () => false;
      circle.onmousedown = (event) => {
        circle.style.position = 'absolute';
        console.log(event);
        function moveAt(event) {
// eslint-disable-next-line no-mixed-operators
          console.log(`${event.pageX - circle.offsetWidth / 2}px`);
          circle.style.transform = `rotate(${20}deg)`;
        }
        document.onmousemove = (event) => {
          moveAt(event);
        };
        circle.onmouseup = () => {
          document.onmousemove = null;
          circle.onmouseup = null;
        };
      };
    },
    methods: {},
  };
</script>
<style>
  .circle {
    background-color: red;
    width: 500px;
    height: 500px;
    border-radius: 50%;
  }

  .str {
    width: 12px;
    height: 100px;
    background-color: black;
    margin: auto;
  }
</style>
