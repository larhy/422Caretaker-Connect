<template>
  <div class="tasks">
    <h1 style="margin-top: 2rem; font-weight: bold">Current Tasks</h1>
    <b-form-group
      style="margin-top: 5rem"
      v-slot="{ ariaDescribedby }"
    >
      <b-form-checkbox
        v-for="option in options"
        v-model="selected"
        :key="option.value"
        :value="option.value"
        :aria-describedby="ariaDescribedby"
        name="todo_items"
        size="lg"
        style="margin-bottom: 1rem"
      >
        {{ option.text }}
      </b-form-checkbox>
    </b-form-group>

    <b-button variant="outline-primary" size="lg" style="margin-top: 4rem">Save</b-button>
  </div>
</template>

<script>

export default {
  name: 'Tasks',
  components: {
  },

  data() {
    return {
        selected: [],
        options: [{text: "Give Jason a bath", value: "0"}, {text: "Remind Alex to do homework", value: "1"}, {text: "Put to sleep at 8pm", value: "2"}],
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


@media screen and (max-width: 768px) {
    
}




</style>
