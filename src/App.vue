<template>
  <div id="app">
    <b-container fluid>
    <SurveySquirrelHeader/>
    <QuestionInput/>
</b-container>
  </div>
</template>

<script>
import SurveySquirrelHeader from './components/SurveySquirrelHeader.vue';
import QuestionInput from './components/QuestionInput.vue';

export default {
  name: 'app',
  components: {
    SurveySquirrelHeader,
    QuestionInput
  }
}
</script>

<style lang="sass">
$font-stack: 'Roboto', sans-serif;

html, body
  height: 100%;

.container-fluid
  height: 100%;
  overflow-y: hidden;

#app 
  font-family: $font-stack;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
</style>

