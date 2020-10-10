<template>
  <v-container>
    <h1 class="text-center">{{ quiz.title }}</h1>
    <div class="question-container">
      <div class="question-box">Q.{{ quiz.question }}</div>

      <!-- 4択 -->
      <div id="answers">
        <v-row>
          <v-col cols="6">
            <v-btn x-large block dark :outlined="selectedAnswer !== 1" color="blue" @click="selectAnswer(1)">A. {{ quiz.answer1 }}</v-btn>
          </v-col>
          <v-col cols="6">
            <v-btn x-large block dark :outlined="selectedAnswer !== 2" color="blue" @click="selectAnswer(2)">B. {{ quiz.answer2 }}</v-btn>
          </v-col>
        </v-row>

        <v-row>
          <v-col cols="6">
            <v-btn x-large block dark :outlined="selectedAnswer !== 3" color="blue" @click="selectAnswer(3)">C. {{ quiz.answer3 }}</v-btn>
          </v-col>
          <v-col cols="6">
            <v-btn x-large block dark :outlined="selectedAnswer !== 4" color="blue" @click="selectAnswer(4)">D. {{ quiz.answer4 }}</v-btn>
          </v-col>
        </v-row>
      </div>

      <div class="answer-btn">
        <v-btn depressed x-large block color="primary" @click.stop="postAnswer">回答する</v-btn>
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

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import axios from 'axios'

@Component
export default class Quiz extends Vue {

  quiz: any = {}
  selectedAnswer: number | null = null
  dialog: boolean = false
  result: any = {}

  async getQuiz(titleId: number, quizId: number) {
    let params: any = {}
    params.title_id = this.$route.params.titleId
    params.quiz_id = this.$route.params.quizId ? this.$route.params.quizId : undefined
    const { data } = await axios.get(`/quiz`, { params })
    return data
  }

  selectAnswer(answer: number) {
    this.selectedAnswer = answer
  }

  // クイズの回答を送信する
  async postAnswer() {
    const params = {
      quiz_id: this.quiz.id,
      answer: this.selectedAnswer
    }
    this.result = await axios.post(`/quiz/answer`, { ...params })
  }

  async mounted() {
    this.quiz = await this.getQuiz(Number(this.$route.params.titleId), Number(this.$route.params.quizId))
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
