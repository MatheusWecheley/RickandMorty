<template>
  
  <router-view/>
</template>

<script>
import HomeView from "./views/HomeView.vue"

export default {
  components: {
    HomeView,
  }
}
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Signika+Negative:wght@300&display=swap');


*{
  margin: 0;
  font-family: 'Signika Negative', sans-serif;
}
</style>
