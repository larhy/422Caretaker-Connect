<template>
  <div class="messages">
    <div style="position: fixed; width: 100vw; z-index: 100; top: 0; height: 10vh; padding-top: 2rem; background: whitesmoke; box-shadow: 0rem 1rem 2rem rgb(0 0 0 / 10%);">
        <h1 style="font-weight: bold">Annie</h1>
    </div>
    <div id="messages_container" style="width: 100vw; height: 90vh">
        <div id="messages_list" style="display:flex; flex-direction:column; height:80%;">
            <div class="chatbox" style="flex: 1; height:100%; overflow: auto; display: flex; flex-direction: column-reverse;">
                <div :class="{message_1: !message.from_user, message_2: message.from_user}" v-for="message in messages" :key="message">
                    <div :class="{message_text1: !message.from_user, message_text2: message.from_user}">{{message.text}}</div>
                    <div class="message_time">{{message.time.toLocaleString()}}</div>
                </div>
            </div>
        </div>
        <div id="message_input" style="height: 20%; overflow: scroll; position: relative">
            <b-form-textarea
            id="textarea"
            v-model="text"
            placeholder="Enter something..."
            rows="3"
            max-rows="6"
            style="position: absolute; bottom: 0"
            v-on:keyup.enter="onEnter"
            ></b-form-textarea>
        </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Messages',
  components: {
  },

  data() {
    return {
        text: "",
        messages: [
            {text: "I'll make sure to pay you for the extra hour", from_user: false, time: new Date('November 30, 2021 18:10:00')},
            {text: "Hey! Could you make sure Alex does his homework tonight, I'll be coming home late arount 7pm tonight. Thank you!", from_user: false, time: new Date('November 30, 2021 18:05:00')},
        ]

    }
  },

  methods: {
    onEnter: function () {
      let new_message = {text: this.text, from_user: true, time: new Date()}
      this.messages.unshift(new_message)
      this.text = ""
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


.message_1 {
    max-width: 50%; left: 1rem; position: relative; padding: 1rem; margin-top: 1rem;
}

.message_text1 {
    background: #E6E5EB; color: black; border-radius: 2rem; padding: 1rem;
}

.message_text2 {
    background: #0B81FF; color: white; border-radius: 2rem; padding: 1rem;
}

.message_time {
    font-size: 0.7rem;
    opacity: 0.8;
    margin-top: 0.5rem;
}

.message_2 {
    max-width: 50%; position: relative; padding: 1rem; margin-top: 1rem; right: 0; float: right;
}

@media screen and (max-width: 768px) {
    
}




</style>
