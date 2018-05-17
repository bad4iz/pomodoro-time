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
  /* eslint-disable no-shadow,no-multiple-empty-lines,no-trailing-spaces,max-len,one-var,no-unused-vars */

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
// eslint-disable-next-line one-var
      const style = getComputedStyle(circle),
        width = style.width.replace('px', ''),
        height = style.height.replace('px', '');
      circle.onmousedown = (event) => {
        circle.style.position = 'absolute';
        console.log(event);

// eslint-disable-next-line no-unused-vars
        function moveAt(event) {
          // console.log((event.layerX - (width / 2)), (event.layerY - (height / 2)));
          const x = event.layerX - (width / 2),
            y = event.layerY - (height / 2);

          console.log((Math.cos(x) - Math.sin(x)) * 360);




// eslint-disable-next-line no-mixed-operators
//           console.log(Math.tan(event.pageX - circle.offsetWidth));

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
