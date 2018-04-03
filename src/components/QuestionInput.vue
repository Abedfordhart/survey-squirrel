<template>
  <div>
    <b-row>
      <b-col class="whats-your-question">
        <h5 class="whats-your-question-text">{{msg}}</h5>
      </b-col>
    </b-row>
    <b-row class="type-question-here row-3">
        <b-col class="user-question">
          <b-form-input
            class="question-input"
            type="text"
            size="lg"
            placeholder="Type question here."
            v-model="newQuestion">
          </b-form-input>
        </b-col>
        <b-col class="save">
          <b-button class="grey-button"</b-button>
        </b-col>
    </b-row>
      <b-row class="type-question-here row-3 added-question">
        <b-col class="user-question">
          <b-form-input
            class="question-input"
            type="text"
            size="lg"
            placeholder="Type question here."
            >
          </b-form-input>
        </b-col>
        <b-col class="save">
          <b-button class="grey-button">Save Question</b-button>
        </b-col>
    </b-row>
    <div>
      <b-row>
        <b-col class="whats-your-answer">
          <h5 class="whats-your-answer-text">Answers</h5>
        </b-col>
      </b-row>
      <b-row class="type-answer-here">
          <b-col class="user-answer">
            <b-form-input
              class="question-input"
              type="text"
              size="lg"
              placeholder="Type answer here."
              v-model="newQuestion"
              >
            </b-form-input>
          </b-col>
          <b-col class="answer-button-div">
            <b-button class="answer-button"><span>Add Another Answer</span></b-button>
          </b-col>
      </b-row>
      <b-row class="type-answer-here">
          <b-col class="user-answer">
            <b-form-input
              class="question-input"
              type="text"
              size="lg"
              placeholder="Type answer here."
              >
            </b-form-input>
          </b-col>
      </b-row>
    </div>
</div>
</template>

<script>
  export default {
    name: 'QuestionInput',
    data: function () {
      return {
        msg: "What's your question?",
        newQuestion: ''
      }
    }
  }
</script>

<style lang="sass">
$font-stack: 'Roboto', sans-serif;
$survey-green: #007480;
$font-weight-lighter: 300;
$font-weight-bolder: 500;

.question-input::-webkit-input-placeholder 
  color: #808080;
  font-family: $font-stack;
  font-weight: $font-weight-lighter;


.question-input:-ms-input-placeholder 
  color: #808080;
  font-family: $font-stack;
  font-weight: $font-weight-lighter;


.question-input:-moz-placeholder 
  color: #808080;
  font-family: $font-stack;
  font-weight: $font-weight-lighter;


.question-input::-moz-placeholder 
  color: #808080;
  font-family: $font-stack;
  font-weight: $font-weight-lighter;

.whats-your-question
  max-width: 957px;
  width: 100%;
  margin-left: auto;
  margin-right: auto;

.user-question
  max-width: 758px;
  height: 60px
  width: 100%;

.whats-your-question-text 
  color: #808080;
  font-size: 22px;
  font-weight: $font-weight-bolder;
  letter-spacing: -0.57px;
  text-align: left;

.type-question-here
  max-width: 957px;
  height: 60px
  width: 100%;
  margin-left: auto;
  margin-right: auto;

.grey-button
  background-color: #F2F2F2;
  border: 1px solid #808080;
  border-radius: 2px;
  width: 125px;
  height: 40px;
  color: #3F3F3F;
  font-size: 14px;
  font-weight: 500;

.row-3
  margin-bottom: 30px;
</style>