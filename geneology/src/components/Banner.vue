<template>
  <v-carousel v-model="model" 
      hide-delimiters
      show-arrows-on-hover
      height="700"
      >
    <v-carousel-item
      v-for="(i, src) in srcs"
      :key="src"
    >
      <v-parallax 
      :src="src" 
      height="700"
      dark
      >
        <v-row
        align="center"
        justify="center"
        >
          <v-col
            class="text-center"
            cols="52"
            >
            <h1 class="text-h4 font-weight-thin mb-4">
              {{i}}
            </h1>
            <h4 class="subheading">
              Сделай это легко вместе с geneology
            </h4>
          </v-col>
        </v-row>
      </v-parallax>
    </v-carousel-item>
  </v-carousel>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: "Banner",

  data: () => ({
    model: 0,
    srcs: {
      'https://media.elitsy.ru/wp-content/uploads/2019/05/fe49bd235a8c19b8ffa580cfa9c76df0.jpg': "Найди своих предков",
      'https://pbs.twimg.com/media/EZB4N8tWAAUnlBd.jpg:large': "Записи 19, 18 и 17-ых веков",
      'https://cp14.nevsepic.com.ua/188/18756/1385073234-be029610.jpg': "Великая Отечественная война",
      'https://img-fotki.yandex.ru/get/897810/156792724.3ae/0_1844d4_54aafb10_orig.jpg': "Первая мировая война",
      'http://друзья-сябры.рф/wp-content/uploads/2020/09/voina.jpg': "Война 1812 года",
    },
  })
})
</script>

