<template>
  <v-container>
    <h1 class="text-center">クイズタイトル</h1>
    <div class="question-container">
      <div class="question-number">Q1</div>
      <div class="question-box">日本で一番高い山の名前は？</div>

      <!-- 4択 -->
      <div id="answers">
        <v-row>
          <v-col cols="6">
            <v-btn x-large block dark color="blue">A. 富士山</v-btn>
          </v-col>
          <v-col cols="6">
            <v-btn x-large block dark outlined color="blue">B. 六甲山</v-btn>
          </v-col>
        </v-row>

        <v-row>
          <v-col cols="6">
            <v-btn x-large block dark outlined color="blue">C. 阿蘇山</v-btn>
          </v-col>
          <v-col cols="6">
            <v-btn x-large block dark outlined color="blue">D. 函館山</v-btn>
          </v-col>
        </v-row>
      </div>

      <div class="answer-btn">
        <v-btn depressed x-large block color="primary" @click.stop="dialog = true">回答する</v-btn>
      </div>

      <v-dialog v-model="dialog" persistent max-width="600">
        <div class="py-8 white">
          <div v-if="true" class="text-center blue--text judge-text">〇正解！</div>
          <div v-else class="text-center red--text judge-text">✖不正解</div>
          <div class="text-center font-weight-bold answer-text">正解は「A. 富士山」</div>
          <div class="py-3 px-6">説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明説明。</div>
          <div class="text-center mb-2">
            <v-btn depressed x-large color="cyan darken-1 white--text" @click.stop="dialog = false">次の問題</v-btn>
          </div>
          <div class="text-center">
            <v-btn text color="primary" @click.stop="dialog = false">やめる</v-btn>
          </div>
        </div>
      </v-dialog>

    </div>

  </v-container>
</template>

<script>
export default {
  data () {
    return {
      dialog: false
    }
  }
}
</script>

<style>
  .judge-text {
    font-size: 40px;
  }

  .answer-text {
    font-size: 22px;
  }

  #answers {
    margin-top: 10px;
  }

  .answer-btn {
    margin-top: 14px;
  }

  .question-container {
    margin: 0px 30px;
  }

  .question-number {
    padding-left: 6px;
    font-size: 30px;
  }

  .question-box {
    padding: 10px;
    border: 2px solid #000;
    height: 220px;
    font-size: 30px;
  }
</style>
