<template>
  <div class="calendar">
    <kalendar :configuration="calendar_settings" :events.sync="events" />
  </div>
</template>

<script>
// @ is an alias to /src
import { Kalendar } from 'kalendar-vue';

export default {
  name: 'Home',
  components: {
	Kalendar,
  },

  data() {
    return {
        calendar_settings: {
            style: 'material_design',
            view_type: 'week',
            cell_height: 20,
            scrollToNow: true,
            start_day: new Date().toISOString(),
            read_only: true,
            day_starts_at: 0,
            day_ends_at: 24,
            overlap: false,
            past_event_creation: true
        },
        events: [
            {
                from: '2020-03-18T18:00:00Z',
                to: '2020-03-18T19:00:00Z',
                data: 'Event 1',
            },
            {
                from: '2020-03-18T19:00:00Z',
                to: '2020-03-18T21:00:00Z',
                data: 'Olive & Friends',
            },
        ],
    }
  },

  methods: {
    login: function (event) {
      // `this` inside methods points to the Vue instance
      alert('Hello ' + this.name + '!')
      // `event` is the native DOM event
      if (event) {
        alert(event.target.tagName)
      }
    }
  }
}
</script>

<style scoped>
@font-face { font-family: 'pumpkin'; src: url('../assets/Spicy Pumpkin.ttf')}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}


</style>
