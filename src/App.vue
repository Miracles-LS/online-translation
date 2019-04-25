<template>
  <div id="app">
    <h1>在线翻译功能</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <!-- 绑定子组件的$emit()传过来的事件 -->
    <translateForm v-on:formSubmit="translateText"></translateForm>
    <h5>{{loadingText}}</h5>
    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
  import TranslateForm from './components/translateForm.vue';
  import TranslateOutput from './components/translateOutput.vue';

  export default {
    name: 'app',
    data() {
      return {
        translatedText: '',
        loadingText: ''
      }
    },
    components: {
      TranslateForm, TranslateOutput
    },
    methods: {
      translateText(text, language) {
        this.loadingText = '请求中...';
        this.translatedText = '';
        this.axios.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190424T085950Z.6471b223f02e36b0.cfb857a2dc952b95d714d3c6a5f5faa3438406d8&text=' + text + '&lang=' + language)
          .then((response) => {
            console.log(response.data.text[0])
            this.translatedText = response.data.text[0];
            this.loadingText = '';
          })
          .catch((error) => {
            console.log(error)
          })
      }
    },
  }
</script>

<style lang="scss">
  #app {
    margin-top: 50px;
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
  }

  h5 {
    margin-top: 10px;
    font-size: 2rem;
  }
</style>