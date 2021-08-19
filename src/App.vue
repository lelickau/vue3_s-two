<template>
  <navbar-item></navbar-item>
  <div class="app">
    <router-view></router-view>
  </div>
</template>
<script>
import NavbarItem from '@/components/UI/NavbarItem.vue';

export default {
  components: { NavbarItem },

}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  color: #22252e;
  font-family: "Nunito", sans-serif;
  font-size: 18px;
  line-height: 25px;
  background-color: #fcfcfd;
}
.title {
  font-size: 22px;
  line-height: 30px;
  font-weight: 700;
  margin-top: 20px;
  margin-bottom: 30px;
}
.app {
  max-width: 1000px;
  border-radius: 10px;
  background-color: #fcfdfd;
  margin: 0 auto;
  padding: 30px;
  margin-top: 35px;
  -webkit-box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
  -moz-box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
  box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
}
</style>