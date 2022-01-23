<template>
  <v-app>
    <Banner/>
    <v-container fluid class="d-flex justify-center mb-6 grey lighten-5 mx-0">
      <Search style="width: 50em"/>
    </v-container>
    <v-container fluid class="d-flex justify-center blue-grey darken-4 mx-0">
      <FirstHomesBlock />
    </v-container>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue'
import Banner from '../components/Banner.vue'
import Search from '../components/Search.vue'
import FirstHomesBlock from '../components/FirstHomesBlock.vue'

export default Vue.extend({
    name: 'Home',

    components: {
      Banner,
      Search,
      FirstHomesBlock,
    },
})
</script>
