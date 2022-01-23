<template>
  <v-app>
    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
import Menu from 'components/Menu.vue'

export default {
  name: 'App',

  data: () => ({
    //
  }),
  components:{
    Menu
  },
};
</script>
