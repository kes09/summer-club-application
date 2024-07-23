<template>
  <the-header title="Summer Clubs"></the-header>
  <learning-survey ></learning-survey>
  <user-experiences></user-experiences>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import LearningSurvey from './components/survey/LearningSurvey.vue';
import UserExperiences from './components/survey/UserExperiences.vue';

export default {
  components: {
    TheHeader,
    LearningSurvey,
    UserExperiences,
  },
  // data() {
  //   return {
  //     savedSurveyResults: [],
  //   };
  // },
  // methods: {
  //   storeSurvey(surveyData) {
  //     const surveyResult = {
  //       name: surveyData.userName,
  //       club: surveyData.club,
  //       email: surveyData.userEmail,
  //       id: new Date().toISOString(),
  //     };
  //     this.savedSurveyResults.push(surveyResult);
  //     console.log(surveyResult);
  //   },
  // },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>