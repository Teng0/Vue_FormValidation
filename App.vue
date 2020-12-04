<template>
  <form action="" @submit.prevent="submit" class="form">
    <MyInput name="UserName" :value="name.value" :rules="{ required:true,min:5 }" @update="update"></MyInput>
    <MyInput name="UserPassword" :value="paswword.value" :rules="{ required:true,min:10 }" @update="update"></MyInput>
    <MyButton backround="darkslateblue" color="white" :disabled="{ username:name.valid,password:paswword.valid }" ></MyButton>
  </form>

</template>

<script>
import MyButton from "./My_button.vue"
import MyInput from "./My_input.vue"
export default {
    components:{
      MyButton,
      MyInput
    },
    data(){
      return {
        name:{
          value:"",
          valid:false
        },
        paswword:{
          value:"",
          valid:false
        },
      }
    },
  methods:{
    update(value){
      if (value.name=="UserName"){
        this.name.value =value.value;
        this.name.valid =value.valid;
      }else{
        this.paswword.value =value.value;
        this.paswword.valid =value.valid;
      }

    },
    submit($evt){

    }
  }
}
</script>

<style>
body{
  font-family: Arial;
}
.form{
  max-width: 400px;
  width: 50%;
}
</style>