<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <Header></Header>
    <Navigation></Navigation>
  </div>
</template>

<script>
import Navigation from "../components/Navigation";
import Header from "../components/Header";

export default {
  name: 'Home',
  components: {
    Navigation,
    Header
  }
}
</script>
