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
// eslint-disable-next-line no-unused-vars
// eslint-disable-next-line one-var
// eslint-disable-next-line no-mixed-operators

    mounted() {
      const circle = document.querySelector('.circle');
      circle.ondragstart = () => false;

      const style = getComputedStyle(circle),
        width = style.width.replace('px', ''),
        height = style.height.replace('px', '');

      circle.onmousedown = (event) => {
        circle.style.position = 'absolute';
        const Xold = event.layerX,
          Yold = event.layerY;


        function moveAt(event) {
          // console.log('two', event.layerX);
          console.log((event.layerX - (width / 2)), (event.layerY - (height / 2)));
          const x = Xold - event.layerX,
            y = Yold - event.layerY;

          const answer = (((Math.sin(x / 500) * Math.cos(y / 500)) + (Math.sin(y / 500) * Math.cos(x / 500))) * 360);
          console.log(answer);


          console.log(Math.tan(event.pageX - circle.offsetWidth));

          circle.style.transform = `rotate(${answer}deg)`;
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
