<template>
    <div>
       <h2>Zajęcia</h2>
       <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
       <meetings-list :meetings="meetings"></meetings-list>
    </div>
</template>

<script>
import NewMeetingForm from "./NewMeetingForm";
import MeetingsList from "./MeetingsList";

export default {
  components: {NewMeetingForm, MeetingsList},
  data() {
      return {
          meetings: []
      };
  },
  methods: {
      addNewMeeting(meeting) {
          this.meetings.push(meeting);
      }
  }
}
</script>
src/meetings/NewMeetingForm.vue

<template>
    <form @submit.prevent="addNewMeeting()">
            <h3>Dodaj nowe spotkanie</h3>
            <label>Nazwa</label>
            <input type="text" v-model="newMeeting.name">
            <label>Opis</label>
            <textarea v-model="newMeeting.description"></textarea>
            <button>Dodaj</button>
        </form>
</template>

<script>
export default {
  data() {
      return {
          newMeeting: {}
      };
  },
  methods: {
      addNewMeeting() {
        this.$emit('added', this.newMeeting);
        this.newMeeting = {};
    }
  }
}
</script>