<template>
    <div class="row" id="translateForm">
        <div class="col-md-8 col-md-offset-2 col-sm-8 col-sm-offset-2 col-xs-8 col-xs-offset-2">
            <form @submit="submitForm" class="well form-inline row">
                <div class="col-md-8">
                    <input class="form-control" type="text" placeholder="请输入需要翻译的内容" v-model="textToTranslate" style="width:100%;">
                </div>
                <div class="col-md-2">
                    <select class="form-control" v-model="language" style="width:100%;">
                        <option value="en">英语</option>
                        <option value="ru">俄语</option>
                        <option value="ko">韩语</option>
                        <option value="ja">日语</option>
                    </select>
                </div>
                <div class="col-md-2">
                    <input class="btn btn-info" type="submit" value="翻译" style="width:100%;">
                </div>
            </form>
        </div>
    </div>
</template>

<script>

    export default {
        name: "translateForm",
        data(){
            return{
                textToTranslate:'',
                language:'',
            }
        },
        methods:{
            submitForm:function(e){
                if(this.textToTranslate.trim() == ''){
                    alert('请输入需要翻译的内容！');
                }else{
                    // alert(this.textToTranslate);
                    this.$emit('formSubmit',this.textToTranslate,this.language)
                }
                e.preventDefault();
            }
        },
        created:function(){
            this.language = "en";
        }
    };
</script>

<style>
</style>
