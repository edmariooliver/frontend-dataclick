<script setup>
  import Materialize from 'materialize-css'
</script>

<template>
  <Navbar/>
  <RouterView />
</template>

<script>

import Navbar from './components/Navbar.vue'

  export default {
    name: 'App',
    components: {
      Navbar
    }
  }
</script>
