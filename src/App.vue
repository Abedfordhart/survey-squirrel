<template>
  <div id="app">
    <b-container fluid>
    <SurveySquirrelHeader/>
</b-container>
  </div>
</template>

<script>
import SurveySquirrelHeader from './components/SurveySquirrelHeader.vue';

export default {
  name: 'app',
  components: {
    SurveySquirrelHeader
  }
}
</script>

<style lang="sass">
$font-stack: 'Roboto', sans-serif;
$survey-green: #007480;
$font-weight-lighter: 300;
$font-weight-bolder: 500;

html, body
  height: 100%

.container-fluid
  height: 100%;
  overflow-y: hidden;

#app 
  font-family: $font-stack;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%
</style>

