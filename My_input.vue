<template>
  <div class="input-wrapper">
    <div class="label">
      <label :for="name">{{name}}</label>
      <div class="Error">{{error}}</div>
    </div>
    <input :id="name" type="text"  :value="value" @input="input">
  </div>
</template>

<script>
export  default {
  props:{
    name:{
      type:String,
      required:true
    },
    rules:{
      type:Object //min , required
    },
    value:{
      type:String
    }
  },
  data(){
    return{
      valid:true,
    }
  },
  computed:{
    error(){
      if (this.value.length ===0){
        this.valid=false;

        return "Requared";
      }else{
        this.valid=true;
      }
      if(this.value.length < this.rules.min){
        this.valid=false;
        return  "Minimum Length is :"+this.rules.min
      }else{
        this.valid=true;
      }
    },
  },
  methods:{
    input($event){
      this.$emit("update",{
        value:$event.target.value,
        name:this.name,
        valid:this.valid,
      })
    }
  }
  
}
</script >

<style scoped>
.input-wrapper{
  display: flex;
  flex-direction: column;
}
.label{
  display: flex;

  justify-content: space-between;
}
.Error{
  color: red;
}
input {
  color: black;
  border :1px solid;
  border-radius: 5px;
  padding: 10px;
  font-size: 16px;
  margin: 5px 0;
}
</style>