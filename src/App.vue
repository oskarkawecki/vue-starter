<template>
  <div>
	<h1>Witaj w systemie zapisów na zajęcia</h1>
	<div v-if="authenticatedEmail != ''">
	<h4>Jesteś zalogowany jako {{ authenticatedEmail }}</h4>
	<a @click="logMeOut()">Wyloguj</a>
  </div>
  <div v-else>
  Wpisz login:
  <input type="text" v-model="email">
  <button @click="logMeIn()">Wchodzę</button>
  </div>
  </div>
</template>

<script>
import "milligram";

export default {
	data() {
		  return {
		    email: '',
		    authenticatedEmail: ''
		  };
		},
	methods: {
		 logMeIn() {
		    this.authenticatedEmail = this.email;
		  },
		  logMeOut() {
			  this.authenticatedEmail = '';
			  this.email = '';
		  }
		}
};

</script>

<style>

</style>
