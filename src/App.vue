<template>
    <div id="app">
        <h1>在线翻译</h1>
        <h5 class="text-muted">简单 / 易用 / 便捷</h5>
        <translateForm v-on:formSubmit="translateText"></translateForm>
        <translateOutput :translateOutputText="translateOutputText"></translateOutput>
    </div>
</template>

<script>
import TranslateForm from "./components/TranslateForm"
import TranslateOutput from "./components/TranslateOutput"

export default {
    name: "app",
    data(){
        return{
            translateOutputText:'',
        }
    },
    components: {
        TranslateForm,TranslateOutput
    },
    methods:{
        translateText:function(text,lang){
            this.$http.get("https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20181019T023845Z.0c364c79ebcb096d.a1616c1e66f0068e2a40c4b4350ae46bf5e7210f&lang="+ lang +"&text=" + text)
                .then((response) => {
                    this.translateOutputText = response.body.text[0];
                })
        }
    }
};
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
</style>
