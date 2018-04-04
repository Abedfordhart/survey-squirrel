<template>
  <div v-if="!submitted">
    <b-row class="row-m2">
    <b-col class="welcome">
      <h1 class="welcome-message" v-if="!done">{{welcome}}</h1>
      <h1 class="welcome-message" v-else>{{review}}</h1>
    </b-col>
  </b-row>
    <b-row>
      <b-col class="whats-your-question">
        <h5 class="whats-your-question-text">{{msg}}</h5>
      </b-col>
    </b-row>
    <b-row class="type-question-here row-3" v-if="questions.length === 0 && !done">
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
          <b-button class="grey-button" @click="saveQuestion" v-if="questions.length === 0">Save Question</b-button>
        </b-col>
    </b-row>
      <b-row class="type-question-here row-3 added-question" v-else-if="questions.length !== 0 && !done" v-for="question in questions" :key="question.id">
        <b-col class="user-question">
          <b-form-input
            class="question-input"
            type="text"
            size="lg"
            :placeholder="question.text"
            readonly>
          </b-form-input>
        </b-col>
        <b-col class="save">
          <b-button class="grey-button" @click="saveQuestion" v-if="questions.length === 0">Save Question</b-button>
        </b-col>
    </b-row>
    <b-row class="type-question-here row-3" v-if="done">
        <b-col class="user-question">
          <b-form-select
            value=""
            class="question-input"
            :options="answers"
            size="lg"
            readonly
            >
              <option value="" slot="first" selected disabled>{{newQuestion}}</option>
          </b-form-select>
        </b-col>
    </b-row>
    <div v-if="questions.length > 0 && !done">
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
              v-model="newAnswer"
              >
            </b-form-input>
          </b-col>
          <b-col class="answer-button-div">
            <b-button class="answer-button" @click="saveAnswer"><span>Add Another Answer</span></b-button>
          </b-col>
      </b-row>
      <b-row class="type-answer-here" v-for="answer in answers" :key="answer.id">
          <b-col class="user-answer">
            <b-form-input
              class="question-input"
              type="text"
              size="lg"
              :placeholder="answer.text"
              readonly
              >
            </b-form-input>
          </b-col>
      </b-row>
    </div>
    <b-row class="done-submit-buttons">
      <b-col>
        <!-- Add Question doesn't have functionality --> 
        <b-button class="grey-button">Add Question</b-button>
        <b-button class="blue-button" @click="handleDone" v-if="!done">Done</b-button>
        <b-button class="submit-button" @click="handleSubmit" v-if="done">Submit</b-button>
      </b-col>
  </b-row>
</div>
<b-row class="survey-created" v-else>
  <b-col>
    <b-row class="start-another">
    <h1 class="survey-created-text">Your survey has been created!</h1>
    </b-row>
    <b-row>
    <b-button class="start-another-button" @click="startAnother">Start Another Survey</b-button>
    </b-row>
  </b-col>  
</b-row>
</template>

<script>
  export default {
    name: 'QuestionInput',
    data: function () {
      return {
        msg: "What's your question?",
        welcome: "Welcome to Survey Squirrel. Let's build a survey!",
        review: "Review Survey",
        newQuestion: '',
        questions: [],
        newAnswer: '',
        answers: [],
        done: false,
        submitted: false
      }
    },
    mounted: function() {
      if (localStorage.getItem('questions')) {
        this.questions = JSON.parse(localStorage.getItem('questions'))
      }
      if (localStorage.getItem('answers')) {
        this.answers = JSON.parse(localStorage.getItem('answers'))
      }
    },
    watch: {
      question: function() {
        localStorage.setItem('newQuestion', JSON.stringify(this.newQuestion))
      },
      questions: function() {
        localStorage.setItem('questions', JSON.stringify(this.questions))
      },
      answer: function() {
        localStorage.setItem('newAnswer', JSON.stringify(this.newAnswer))
      },
      answers: function() {
        localStorage.setItem('answers', JSON.stringify(this.answers))
      }
    },
    methods: {
      saveQuestion: function() {
        this.questions.push({text: this.newQuestion})
        this.msg = 'Question 1'
      },
      saveAnswer: function() {
        this.answers.push({text: this.newAnswer})
      },
      handleDone: function() {
        this.done = !this.done
      },
      handleSubmit: function() {
        this.submitted = !this.submitted
      },
      startAnother: function() {
        localStorage.clear()
        location.reload()
      }
    }
  }
</script>

<style lang="sass">
$font-stack: 'Roboto', sans-serif;
$survey-green: #007480;
$survey-light-grey: #808080;
$button-grey: #F2F2F2;
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
  font-weight: $font-weight-lighter;
  letter-spacing: -0.85px;
  position: relative;
  top: 50%;
  transform: translateY(-50%);

.question-input::-webkit-input-placeholder 
  color: $survey-light-grey;
  font-family: $font-stack;
  font-weight: $font-weight-lighter;


.question-input:-ms-input-placeholder 
  color: $survey-light-grey;
  font-family: $font-stack;
  font-weight: $font-weight-lighter;


.question-input:-moz-placeholder 
  color: $survey-light-grey;
  font-family: $font-stack;
  font-weight: $font-weight-lighter;


.question-input::-moz-placeholder 
  color: $survey-light-grey;
  font-family: $font-stack;
  font-weight: $font-weight-lighter;

.whats-your-question
  max-width: 957px;
  width: 100%;
  margin-left: auto;
  margin-right: auto;

.whats-your-question-text 
  color: $survey-light-grey;
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

.whats-your-answer
  max-width: 600px;
  width: 100%;
  margin-left: auto;
  margin-right: auto;

.whats-your-answer-text 
  color: $survey-light-grey;
  ont-size: 22px;
  font-weight: $font-weight-bolder;
  letter-spacing: -0.57px;
  text-align: left;

.type-answer-here
  max-width: 600px;
  height: 60px;
  width: 100%;
  margin-left: auto;
  margin-right: auto;

.user-question
  max-width: 758px;
  height: 60px;
  width: 100%;

.user-answer
  max-width: 353px;
  height: 60px
  width: 100%;

.grey-button
  background-color: $button-grey;
  border: 1px solid $survey-light-grey;
  border-radius: 2px;
  width: 125px;
  height: 40px;
  color: #3F3F3F;
  font-size: 14px;
  font-weight: 500;

.answer-button
  background-color: $button-grey;
  border: 1px solid $survey-light-grey;
  border-radius: 2px;
  height: 40px;
  color: #3F3F3F;
  font-size: 14px;
  font-weight: 500;

.answer-button-div
  max-width: 155px;

.save
  max-width: 125px;
  height: 40px;

.row-3
  margin-bottom: 30px;

.blue-button
  background-color: #009BAB;
  border: 1px solid #007480;
  border-radius: 2px;
  width: 125px;
  height: 40px;
  color: #FFFFFF;
  font-size: 14px;
  font-weight: 500;

.submit-button
  background-color: #4A90E2;
  border: 1px solid #4A90E2;
  border-radius: 2px;
  width: 125px;
  height: 40px;
  color: #FFFFFF;
  font-size: 14px;
  font-weight: 500;

.done-submit-buttons
  position: fixed;
  bottom: 33px;
  right: 45px;

.start-another-button
  background-color: #4A90E2;
  border: 1px solid #4A90E2;
  border-radius: 2px;
  height: 40px;
  color: #FFFFFF;
  font-size: 14px;
  font-weight: 500;
  margin-left: auto;
  margin-right: auto;

.survey-created
  background-color: #FFFFFF;
  border: 1px solid #979797;
  max-width: 1007px;
  height: 267px;
  margin-left: auto;
  margin-right: auto;

.survey-created-text
  color: #3F3F3F;
  font-family: Roboto;
  font-size: 42px;
  font-weight: 300;
  letter-spacing: -0.85px;
  margin-right: auto;
  margin-left: auto;

.start-another
  height: 114px;
  margin: 38px;
</style>