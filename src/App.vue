<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style lang="scss">
  @import url('./assets/fonts/fonts.css');
  
  body {
    margin: 0;
  }
  p, h2, h3 {
    margin: 0;
  }
  #app {
    font-family: 'RotondaC';
  }
  .bold, h2, h3 {
    font-family: 'RotondaC Bold';
  }
  .p-rel {
    position: relative;
  }
  .text-green {
    color: #7db945;
  }
  @media (min-width: 0px) and (max-width: 280px) {
    #app {
      min-width: 280px;
      overflow-x: auto;
    }
  }
</style>
