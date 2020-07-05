<template>
  <v-container>
    <h1 class="text-center">クイズ一覧</h1>
    <h2 class="text-center">新着</h2>
    <v-row>
      <v-col
        v-for="(item, i) in items"
        :key="i"
        cols="12"
      >
        <v-card
          :color="item.color"
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
                v-text="item.title"
              ></v-card-title>

              <v-card-subtitle v-text="item.description"></v-card-subtitle>
            </div>
          </div>
        </v-card>
      </v-col>

      <v-col cols="12">
        <v-col cols="12">
          <h1 class="text-center">カテゴリー</h1>
        </v-col>
        <v-row>
          <v-col v-for="(item, i) in 8" cols="3" :key="i">
            <v-card>
              <v-img
                src="../assets/logo.png"
                class="white--text align-end"
                gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
                height="200px"
              >
              </v-img>
              <v-card-title>カテゴリー名</v-card-title>
            </v-card>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {},
  data: () => ({
    items: [
      {
        color: '#FFF',
        src: '../assets/logo.png',
        title: 'クイズタイトル',
        description: 'Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.'
      },
      {
        color: '#FFF',
        src: 'https://cdn.vuetifyjs.com/images/cards/halcyon.png',
        title: 'クイズタイトル',
        description: 'Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.'
      },
      {
        color: '#FFF',
        src: 'https://cdn.vuetifyjs.com/images/cards/halcyon.png',
        title: 'クイズタイトル',
        description: 'Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.'
      }
    ]
  })
}
</script>
