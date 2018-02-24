<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单 / 易用 / 便捷</h5>
    <translateForm @getValue="getValue"></translateForm>
    <translateOutput v-text="translatedText" class="mt20"></translateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'
export default {
  name: 'App',
  data () {
    return {
      translatedText:''
    }
  },
  components:{
    TranslateForm,TranslateOutput
  },
  methods:{
    getValue: function(value,language){
      this.$http.get(
        'https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180224T080354Z.5a33766701191b81.965ffe57fd6987e57af8d187a4a7a5c6ed1d42af&lang='+language+'&text='+value)
        .then((response)=>{
          this.translatedText=response.body.text[0];
        });
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{color: #666;}
h5{color:#999;}
button,a,input{outline: none;}
.mt20{margin-top: 20px;}
</style>
