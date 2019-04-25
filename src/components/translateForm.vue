<template>
  <div class="row" id="translateForm">
    <div class="col-md-6 col-md-offset-3">
      <form class="well form-inline" v-on:submit="formSubmit" id="transForm">
        <div class="form-group">
          <input class="form-control" type="text" placeholder="请输入需要翻译的内容" v-model="textToTranslate">
        </div>
        <div class="form-group">
          <select class="form-control" v-model="language">
              <option disabled value="">请选择语言</option>
              <option value="en">English</option>
              <option value="sr">Serbian</option>
              <option value="de">German</option>
              <option value="ko">Korean</option>
              <option value="ja">Japanese</option>
          </select>
        </div>
        <div class="form-group">        
          <input type="submit" value="翻译" class="btn btn-primary">
        </div>
      </form>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'translateForm',
    data() {
        return {
            textToTranslate:'',
            language:''
        }
    },
    methods:{
        formSubmit(e){
            //父传子组件的方法--$emit()
            this.$emit('formSubmit',this.textToTranslate,this.language);
            e.preventDefault();//阻止默认事件，submit提交后默认会刷新页面
        },
        mounted() {
          this.language='en';
        },
    }
  }
</script>

<style lang="scss">
  #translateForm{
    justify-content: center;
  }
  #transForm{
    background-color: #eee;
    justify-content: center;
    border: 1px solid #eee;
    border-radius: 10px;
    padding: 20px 0;
  }
  .form-control{
    margin-right:10px;
  }
</style>
