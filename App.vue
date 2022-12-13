<template>
  <div id="app">
    <input v-model="username" placeholder="masukkan username..."/>
    <input v-model="password" placeholder="masukkan password..."/>
    <button v-on:click="simpan()">Simpan</button>
  </div>
</template>

<script>

import {db} from './db'

export default {
  name: 'App',
  data(){
    return{
      username:'',
      password:''
    }
  },
  methods:{
    simpan(){
      //db.collection('chatting').add({username: this.username, password: this.password});
      db.collection('chatting').doc(this.username+this.password).set({username: this.username, password: this.password});
      this.username = '';
      this.password = '';
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
