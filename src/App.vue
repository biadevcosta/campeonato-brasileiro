<template>
  <v-app>
      <AppTopBar/>

    <v-main>
        <MeuInicio/>
    </v-main>
  </v-app>
</template>

<script>

import AppTopBar from './components/shared/AppTopBar.vue';
import MeuInicio from './components/MeuInicio.vue';


export default {
  name: 'App',
  components: {
    MeuInicio,
    AppTopBar,
  },
};
</script>


<style>

</style>
