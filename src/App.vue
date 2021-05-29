<template>
  <div>
	<h1>Witaj w systemie zapisów na zajęcia</h1>
	<div v-if="authenticatedEmail != ''">
	
	<meeting-page></meeting-page>
	
	<h4>Jesteś zalogowany jako {{ authenticatedEmail }}</h4>
	<a @click="logMeOut()">Wyloguj</a>
  </div>
  <div v-else>
	<login-form @login="logMeIn($event)"></login-form>
  </div>
  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
import MeetingPage from "./meetings/MeetingPage";

export default {
	components: {LoginForm, MeetingPage},
	data() {
		  return {
		    authenticatedEmail: ''
		  };
		},
	methods: {
		 logMeIn(username) {
		    this.authenticatedEmail = username;
		  },
		  logMeOut() {
			  this.authenticatedEmail = '';
		  }
		}
};

</script>

<style>

</style>
