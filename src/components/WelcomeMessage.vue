<template>
  <b-row class="row-m2">
    <b-col class="welcome">
      <h1 class="welcome-message">{{welcome}}</h1>
    </b-col>
  </b-row>
</template>

<script>
  export default {
    name: 'WelcomeMessage',
    data () {
      return {
        welcome: "Welcome to Survey Squirrel. Let's Build A Survey!",
        review: "Review Survey"
      }
    }
  }
</script>

<style lang="sass">

$font-stack: 'Roboto', sans-serif;
$survey-green: #007480;
$font-weight-lighter: 300;
$font-weight-bolder: 500;

.row-m2
  margin-bottom: 56px;

.welcome
  border: 1px solid #979797;
  max-width: 1007px;
  height: 137px;
  width: 100%;
  margin-left: auto;
  margin-right: auto;

.welcome-message
  color: #3F3F3F;
  font-size: 42px
  font-weight: $font-weight-lighter
  letter-spacing: -0.85px;
  position: relative;
  top: 50%;
  transform: translateY(-50%);
  
</style>