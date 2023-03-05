<template>
  <navbar/>
  <router-view/>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css';
import 'bootstrap/dist/js/bootstrap';
import navbar from './components/navbar';

export default {
  name: "App",
  components: {
    navbar
  }
}
</script>


<style>

</style>
