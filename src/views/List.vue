<template>
  <v-container>
    <h1 class="text-center">クイズ一覧</h1>
    <h2 class="text-center">{{ categoryName }}</h2>
    <v-row>
      <v-col
        v-for="(title, i) in titles"
        :key="i"
        cols="12"
      >
        <v-card
          @click="$router.push('/quiz/' + title.id)"
        >
          <div class="d-flex">
            <v-avatar
              class="ma-3"
              size="110"
              tile
            >
              <v-img src="../assets/logo.png"></v-img>
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

      <v-col cols="12" >
        <div class="text-center">
          <v-pagination
            v-model="page"
            :length="total"
            @input="onPagenationClick()"
          ></v-pagination>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import axios from 'axios'

@Component
export default class Home extends Vue {
  categoryName = null
  titles = []
  page = 1
  total = 0

  async getTitlesInfomation(categoryId: number, page: number) {
    const params = {
      category_id: categoryId,
      page: page
    }
    const { data } = await axios.get('/titles', { params })
    this.titles = data.data
    this.total = data.total
    this.page = data.current_page
  }

  async getCategory(categoryId: number) {
    const params = {
      category_id: categoryId
    }
    const { data } = await axios.get('/category', { params })
    this.categoryName = data.name
  }

  async onPagenationClick() {
    await this.getTitlesInfomation(Number(this.$route.params.id), this.page)
  }

  async mounted() {
    await this.getTitlesInfomation(Number(this.$route.params.id), this.page)
    await this.getCategory(Number(this.$route.params.id))
  }
}
</script>
