<script >
import { RouterLink, RouterView } from 'vue-router'
import navBarVue from './components/navBar.vue';

export default{
 
 components :{ navBarVue, }
}

</script>

<template>
<navBarVue/>

  <RouterView />
</template>

<style >
html{
  scroll-behavior: smooth;
}
</style>
