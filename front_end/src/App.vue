<template>
  <v-app>
    <v-app-bar
      app
      color="#114856"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="logo.png"
          transition="scale-transition"
          width="60"
        />

        DALICODES' LOAN DETECTION SYSTEM
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://www.youtube.com/channel/UCzSlSeJ4XH4bWH79DKmIxjg"
        target="_blank"
        text
      >
        <span class="mr-2">Subscribe here</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <HelloWorld/>
      <QuestionContainer :questions="my_questions" :question_len="question_len"/>
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import QuestionContainer from './components/QuestionContainer';
import questions from '../questions'

export default {
  name: 'App',

  components: {
    HelloWorld,
    QuestionContainer
  },

  data: () => ({
    my_questions: questions.individual_questions,
    question_len: questions.individual_questions.length
  }),
  // created() {
  //   console.log(questions['individual_questions'].length)
  // }
};
</script>
