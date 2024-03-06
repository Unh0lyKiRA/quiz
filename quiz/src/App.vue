<template>
  <div class="ctr">
    <transition name="fade" mode="out-in">
      <questions
        v-if="questionsAnswered < questions.length"
        :questions="questions"
        :questionsAnswered="questionsAnswered"
        @question-answered="questionAnswered"
      />
      <result v-else :results="results" :totalCorrect="totalCorrect" />
    </transition>

    <button
      type="button"
      class="reset-btn"
      @click.prevent="reset"
      v-if="questionsAnswered === questions.length"
    >
      Reset
    </button>
  </div>
</template>

<script>
import Questions from "./components/Questions.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: {
    Questions,
    Result,
  },
  data() {
    return {
  questionsAnswered: 0,
  totalCorrect: 0,
  questions: [
    {
      q: "2 + 2 は何ですか？",
      answers: [
        {
          text: "4",
          is_correct: true,
        },
        {
          text: "3",
          is_correct: false,
        },
        {
          text: "魚",
          is_correct: false,
        },
        {
          text: "5",
          is_correct: false,
        },
      ],
    },
    {
      q: '「 Banana 」の中には何文字ありますか？',
      answers: [
        {
          text: "5",
          is_correct: false,
        },
        {
          text: "7",
          is_correct: false,
        },
        {
          text: "6",
          is_correct: true,
        },
        {
          text: "12",
          is_correct: false,
        },
      ],
    },
    {
      q: "欠けている文字を見つけてください：C_ke",
      answers: [
        {
          text: "e",
          is_correct: false,
        },
        {
          text: "a",
          is_correct: true,
        },
        {
          text: "i",
          is_correct: false,
        },
      ],
    },
    {
      q: "3 × 4 は何ですか？",
      answers: [
        {
          text: "7",
          is_correct: false,
        },
        {
          text: "12",
          is_correct: true,
        },
        {
          text: "9",
          is_correct: false,
        },
        {
          text: "16",
          is_correct: false,
        },
      ],
    },
    {
      q: '「こんにちは」を英語で言うと何ですか？',
      answers: [
        {
          text: "Hello",
          is_correct: true,
        },
        {
          text: "Goodbye",
          is_correct: false,
        },
        {
          text: "Thank you",
          is_correct: false,
        },
        {
          text: "Yes",
          is_correct: false,
        },
      ],
    },
    {
      q: "100 ÷ 5 は何ですか？",
      answers: [
        {
          text: "20",
          is_correct: true,
        },
        {
          text: "25",
          is_correct: false,
        },
        {
          text: "10",
          is_correct: false,
        },
        {
          text: "15",
          is_correct: false,
        },
      ],
    },
    {
      q: "日本の首都は何ですか？",
      answers: [
        {
          text: "Seoul",
          is_correct: false,
        },
        {
          text: "Beijing",
          is_correct: false,
        },
        {
          text: "Tokyo",
          is_correct: true,
        },
        {
          text: "Bangkok",
          is_correct: false,
        },
      ],
    },
    {
      q: '「ありがとう」を英語で言うと何ですか？',
      answers: [
        {
          text: "Hello",
          is_correct: false,
        },
        {
          text: "Goodbye",
          is_correct: false,
        },
        {
          text: "Thank you",
          is_correct: true,
        },
        {
          text: "Yes",
          is_correct: false,
        },
      ],
    },
  ],
  results: [
    {
      min: 0,
      max: 3,
      title: "もう一度やってみてください！",
      desc: "もう少し勉強をして、成功するかもしれません！",
    },
    {
      min: 5,
      max: 8,
      title: "わあ、あなたは天才ですね！",
      desc: "勉強が確実に報われています！",
    },
  ],
};


  },
  methods: {
    questionAnswered(is_correct) {
      if (is_correct) {
        this.totalCorrect++;
      }

      this.questionsAnswered++;
    },
    reset() {
      this.questionsAnswered = 0;
      this.totalCorrect = 0;
    },
  },
};
</script>
