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
        <v-btn depressed x-large block color="primary">回答する</v-btn>
      </div>

    </div>

  </v-container>
</template>

<style>
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
