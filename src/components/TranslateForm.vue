<template>
  <div class="translateform">
    <form @submit="formSubmit">
        <input type="text" v-model="textToTranslate" value="" placeholder="请输入需要翻译的内容" />
        <select v-model="language">
            <option value="en">English</option>
            <option value="ja">Japanese</option>
            <option value="kn">Kannada</option>
            <option value="ko">Korean</option>
            <option value="la">Latin</option>
        </select>
        <input type="submit" value="翻译" class="btn">
    </form>
  </div>
</template>

<script>
export default {
  name: 'translateform',
  data () {
    return {
      textToTranslate:'',
      language:''
    }
  },
  methods:{
    formSubmit: function(e){
      // alert(this.textToTranslate);
      this.$emit('getValue',this.textToTranslate,this.language);
      e.preventDefault();
    }
  },
  created: function(){
    this.language = 'en';
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input{height: 28px; padding: 0; border: 1px solid rgb(169, 169, 169); padding: 0 10px;}
select,.btn{height: 30px;}
.btn{
    width: 80px;
    background: #008cff;
    color: #fff;
    border: none;
    cursor: pointer;
}
.translateform{
  width: 500px;
  margin: 0 auto;
  padding: 30px 0;
  background: #eee;
  border-radius: 10px;
}
</style>