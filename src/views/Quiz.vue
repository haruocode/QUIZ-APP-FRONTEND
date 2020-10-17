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
          <div v-if="selectedAnswer === Number(result.answer)" class="text-center blue--text judge-text">〇正解！</div>
          <div v-else class="text-center red--text judge-text">✖不正解</div>
          <div class="text-center font-weight-bold answer-text">正解は「{{ answerLabel }}」</div>
          <div class="py-3 px-6">{{ result.description }}</div>
          <div class="text-center mb-2">
            <v-btn v-if="result.next_quiz_id" depressed x-large color="cyan darken-1 white--text" @click.stop="goToNextQuiz">次の問題</v-btn>
          </div>
          <div class="text-center">
            <v-btn text color="primary" @click.stop="$router.push('/')">トップページへ</v-btn>
          </div>
        </div>
      </v-dialog>

    </div>

  </v-container>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class Quiz extends Vue {

  quiz: any = {}
  selectedAnswer: number | null = null
  dialog: boolean = false
  result: any = {
    answer: null,
    description: null,
    next_quiz_id: null
  }

  async getQuiz() {
    let params: any = {}
    params.title_id = this.$route.params.titleId
    params.quiz_id = this.$route.params.quizId ? this.$route.params.quizId : undefined
    const { data } = await this.axios.get(`/quiz`, { params })
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
    const { data } = await this.axios.post(`/quiz/answer`, { ...params })
    this.result = data
    this.dialog = true
  }

  get answerLabel() {
    return eval('this.quiz.answer' + this.result.answer)
  }

  goToNextQuiz() {
    this.dialog = false
    if(this.result.next_quiz_id !== null) {
      this.$router.push('/quiz/' + this.$route.params.titleId + '/' + this.result.next_quiz_id)
    }
  }

  async mounted() {
    this.quiz = await this.getQuiz()
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
