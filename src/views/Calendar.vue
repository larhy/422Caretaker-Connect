<template>
  <div class="calendar">
    <kalendar :configuration="calendar_settings" :events.sync="events" />
  </div>
</template>

<script>
// @ is an alias to /src
import { Kalendar } from 'kalendar-vue';

export default {
  name: 'Calendar',
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
                from: '2021-11-29T12:00:00Z',
                to: '2021-11-29T18:00:00Z',
                data: 'Annie Jacob: 3001 Taylor Street Chicago, IL 60607',
            },
            {
                from: '2021-12-01T12:00:00Z',
                to: '2021-12-01T18:00:00Z',
                data: 'Annie Jacob: 3001 Taylor Street Chicago, IL 60607',
            },
            {
                from: '2021-12-03T12:00:00Z',
                to: '2021-12-03T18:00:00Z',
                data: 'Annie Jacob: 3001 Taylor Street Chicago, IL 60607',
            },
            {
                from: '2021-12-06T12:00:00Z',
                to: '2021-12-06T18:00:00Z',
                data: 'Annie Jacob: 3001 Taylor Street Chicago, IL 60607',
            },
            {
                from: '2021-12-08T12:00:00Z',
                to: '2021-12-08T18:00:00Z',
                data: 'Annie Jacob: 3001 Taylor Street Chicago, IL 60607',
            },
            {
                from: '2021-12-10T12:00:00Z',
                to: '2021-12-10T18:00:00Z',
                data: 'Annie Jacob: 3001 Taylor Street Chicago, IL 60607',
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

<style>

.kalendar-cell .selected .has-events {
  font-size: 0.5rem !important;
}

.kalendar-cell {
  font-size: 0.5rem !important;
}



.created-event {
    font-size: 0.5rem !important;
}

@media screen and (max-width: 768px) {
  h4 {
    font-size: 0.5rem !important;
  }

  .created-event {
    font-size: 0.5rem !important;
  }
} 
</style>