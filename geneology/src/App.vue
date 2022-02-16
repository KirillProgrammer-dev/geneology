<template>
  <v-app>
    <Menu/>
    <v-main>
      <router-view :registrate="registrate"/>
    </v-main>
  </v-app>
</template>

<script>
import Menu from '../src/components/Menu.vue'

export default {
  name: 'App',
  data: () => ({
    registrate:false,
  }),
  components:{
    Menu
  },
  mounted() {
      let id = localStorage.getItem("id");
      if (id != undefined){
        this.registrate = id;
      } else {
        this.registrate = false;
      }
  }
  
};
</script>
