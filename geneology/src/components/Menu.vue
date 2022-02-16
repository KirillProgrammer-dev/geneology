<template>
    <v-navigation-drawer
        color="deep-orange accent-3 white--text"
        dark
        expand-on-hover
        hide-overlay
        permanent
        right
        absolute
        fixed
      >
        <v-list
            nav 
            shaped
            dense
        >
          <v-list-item two-line>
            <v-list-item-avatar>
              <img src="https://pixabay.com/get/ge26080380786fee529d289673c2470926cf70639430a5a94c262d0748a830e68779650c3b2c0d790c09ca3f773e22132_1280.jpg">
            </v-list-item-avatar>
            <v-list-item-content>
              <v-list-item-title class="font-weight-black">Кенигсберг Кирилл</v-list-item-title>
              <v-list-item-subtitle>14 лет</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <v-divider class="my-3" />
          <v-list-item v-if="registrate" @click="logOut()">
            <v-list-item-icon>
              <v-icon>mdi-logout</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title class="text-left">Выйти</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <div v-else>
            <v-list-item link to="/login">
              <v-list-item-icon>
                <v-icon>mdi-login</v-icon>
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title class="text-left">Войти</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item link to="/registration">
              <v-list-item-icon>
                <v-icon>mdi-account-plus</v-icon>
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title class="text-left">Регистрация</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </div>
          <v-list-item :to="'/'">
            <v-list-item-icon>
              <v-icon> mdi-home-outline </v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title class="text-left">Главная</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
           <v-list-item :to="'/profile'" v-if="registrate">
            <v-list-item-icon>
              <v-icon> mdi-account-outline </v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title class="text-left">Мой профиль</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
           <v-list-item :to="'/search'">
            <v-list-item-icon>
              <v-icon> mdi-account-multiple-plus-outline </v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title class="text-left">Дугие профили</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
    name: "Menu",
    data: () => ({
    }),
    props:["registrate"],
    mounted(){
      console.log(this.colors);
    }
})
</script>
