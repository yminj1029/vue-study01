<template>
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">id: </label>
      <input id="username" type="text" v-model="username"> 
    </div>
    <div>
      <label for="password">pw: </label>
      <input id="password" type="password" v-model="password">
    </div>
    <button type="submit">Login</button>
  </form>
</template>

<script>
import axios from 'axios'
export default {
  //컴포넌트간 데이터를 서로 참조하여 공유되지 않게 function을 연결해서 새 객체를 돌려줌
  data:function(){
    return {
      username:'',
      password:''
    }
  },
  methods:{
    submitForm:function(){
      // event.preventDefault();
      console.log(this.username, this.password)
      var url='https://jsonplaceholder.typicode.com/users'
      var data = {
        username:this.username,
        password: this.password
      }
      axios.post(url, data).then(function(response){
        console.log('성공했습니다.',response)
      }).catch(function(error){
        console.log('실패했습니다.',error)
      });
    }
  }
}
</script>

<style>

</style>