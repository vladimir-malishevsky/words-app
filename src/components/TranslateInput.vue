<template>
  <div class="translate-block">
    <div class="translate-block__word">{{ word[wordLang] }}</div>
    <div class="translate-block__answer" @keydown.enter="enterWord()">
      <input type="text" class="translate-block__input" v-model="answer">
      <div class="translate-block__error" v-if="answerError">{{answerError}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TranslateInput",
  data(){
    return {
      langList: [
        {key: 'uk', value: 'Ukrainian'},
        {key: 'ru', value: 'Russian'},
        {key: 'en', value: 'English'},
      ],
      wordList: [
        {en: 'Place', ru: 'Место'},
        {en: 'Key', ru: 'Ключ'},
        {en: 'Name', ru: 'Имя'},
      ],
      iterator: this.wordsIterator(),
      word: '',
      answer: '',
      wordLang: 'en',
      answerLang: 'ru',
      answerError: ''
    }
  },
  methods: {
    wordsIterator(){
      let nextIndex = 0;
      return {
        next: () => {
          if (nextIndex < this.wordList.length){
            return this.wordList[nextIndex++]
          } else {
            nextIndex = 0
            return this.wordList[nextIndex++]
          }
        }
      }
    },
    enterWord(event){
      let ask = this.word[this.answerLang].toLowerCase()
      let answer = this.answer.toLowerCase()

      if (ask === answer){
        this.word = this.word = this.iterator.next()
        this.answer = '';
        this.answerError = ''
      } else {
        let matches = 0;
        for (let i = 0; i < ask.length; i++){
          if (ask[i] === answer[i]){
            matches++
          }
        }
        if (ask.length - matches <= 1){
          this.answerError = 'Близко'
        } else {
          this.answerError = 'Попробуй ещё раз'
        }
        this.answer = '';
      }
    }
  },
  created() {
    this.word = this.iterator.next()
  }
}
</script>

<style scoped lang="scss">

@import "../assets/scss/Mixins/BreakpointsMixin";

.translate-block {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  .translate-block__word {
    width: 100%;
    height: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    background: pink;
    color: #2C3E50;
    line-height: 150px;
    font-size: 10rem;
    font-weight: bold;
    @include lg {
      font-size: 8rem;
    }
    @include md {
      font-size: 6rem;
    }
    @include sm {
      font-size: 4rem;
    }
  }
  .translate-block__answer {
      width: 100%;
      height: 50%;
      position: relative;
      display: flex;

    .translate-block__input {
      background: #2C3E50;
      color: pink;
      outline: none;
      text-align: center;
      border: none;
      height: 100%;
      width: 100%;
      font-family: "Times New Roman", sans-serif;
      font-weight: bold;
      font-size: 5rem;
      @include lg {
        font-size: 4rem;
      }
      @include md {
        font-size: 3rem;
      }
      @include sm {
        font-size: 2rem;
      }
    }

    .translate-block__error {
      color: red;
      position: absolute;
      bottom: 20%;
      left: 50%;
      transform: translateX(-50%);
    }
  }
}
</style>