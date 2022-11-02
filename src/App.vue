<template>


  <div class="container-view">

    <router-view name="sideBar" class="Admin-sideBar"></router-view>

    <div class="container-right">
      <router-view name="navBar"></router-view>
      <router-view name="main" class="Admin-main"></router-view>
    </div>
  </div>



  <div>
    <router-view>
    </router-view>
  </div>

</template>

<style scoped>
@import "./assets/css/estructura.css";
</style>


