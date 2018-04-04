<template>
  <b-row class="row-m">
    <b-col class="survey-title">
      <h1 class="title-message">Survey Squirrel</h1>
    </b-col>
  </b-row>
</template>

<script>
  export default {
    name: 'SurveySquirrelHeader'
  }
</script>

<style lang="sass">
$font-stack: 'Roboto', sans-serif;
$survey-green: #007480;
$font-weight-lighter: 300;
$font-weight-bolder: 500;

.survey-title 
  background-color: $survey-green;
  height: 99px
  text-align: center;
  max-width: 1440px
  width: 100%
  margin-left: auto;
  margin-right: auto;

.row-m
  margin-bottom: 142px;

.title-message 
  color: #FFFFFF;;
  font-size: 52px;
  font-weight: $font-weight-lighter;
  letter-spacing: -1.06px;
  position: relative;
  top: 50%;
  transform: translateY(-50%);
</style>