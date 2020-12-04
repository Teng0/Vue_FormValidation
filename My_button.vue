<template>
  <button :style="{backgroundColor:backround,color}" :disabled="{isDisabled}" :class="{'disabled-button':isDisabled}">Button</button>
</template>

<script>

export default {
  props:{
    backround:{
      type:String
    },
    color:{
      type:String
    },
    disabled:{
      type:Object//username/password
    },

  },

  computed:{
    isDisabled(){
      if (!this.disabled.username){
        return true
      }else if (!this.disabled.password){
        return true
      }else {
        return false
      }
    }
  }
}
</script>

<style scoped>
  button {
    background: none;
    color: black;
    border :none;
    border-radius: 5px;
    padding: 10px 40px;
    font-size: 16px;
    cursor: pointer;

  }
  button:hover {
    filter: brightness(150%);
  }
  .disabled-button{
    opacity: 0.5;
  }
</style>