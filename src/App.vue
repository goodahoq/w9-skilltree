<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
    name: 'App'
}
</script>

<style lang="scss">
@import "./styles/variables";
body {
  background-image: linear-gradient(to right, $bg, $bg-dark, $bg);
  font-family: "Roboto";
  color: $w;
  font-size: 16px;
}
* {
  box-sizing: border-box;
}
button:focus {
  outline: none;
}
h1 {
  font-size: 48px;
  font-style: italic;
  font-weight: bold;
}
h2 {
  font-size: 36px;
  font-weight: bold;
}
.remark {
  font-size: 14px;
}
</style>
