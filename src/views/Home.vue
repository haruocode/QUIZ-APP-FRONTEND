<template>
  <v-container>
    <h1 class="text-center">クイズ一覧</h1>
    <h2 class="text-center">新着</h2>
    <v-row>
      <v-col
        v-for="(title, i) in newTitles"
        :key="i"
        cols="12"
      >
        <v-card
          :color="title.color"
          @click="$router.push('/quiz/' + title.id)"
        >
          <div class="d-flex">
            <v-avatar
              class="ma-3"
              size="110"
              tile
            >
              <v-img :src="title.thumbnail"></v-img>
            </v-avatar>
            <div>
              <v-card-title
                class="headline"
                v-text="title.title"
              ></v-card-title>

              <v-card-subtitle v-text="title.description"></v-card-subtitle>
            </div>
          </div>
        </v-card>
      </v-col>

      <v-col cols="12">
        <v-col cols="12">
          <h1 class="text-center">カテゴリー</h1>
        </v-col>
        <v-row>
          <v-col v-for="(category, i) in categories" cols="3" :key="i">
            <v-card
              @click="$router.push('/list/' + category.id)"
            >
              <v-img
                :src="category.thumbnail"
                class="white--text align-end"
                gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
                height="200px"
              >
              </v-img>
              <v-card-title>{{ category.name }}</v-card-title>
            </v-card>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class Home extends Vue {
  newTitles: any = []
  categories: any = []

  async getNewTitles() {
    const { data } = await this.axios.get('/titles/new')
    return data
  }

  async getCategories() {
    const { data } = await this.axios.get('/categories')
    return data
  }

  async mounted() {
    // 新着タイトル一覧取得
    this.newTitles = await this.getNewTitles()
    // カテゴリ一覧取得
    this.categories = await this.getCategories()
  }
}
</script>
