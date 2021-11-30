<template>
  <div class="profile">
    <div id="profile_circle">
        <b-icon icon="person" scale="3" aria-hidden="true"></b-icon>
    </div>
    <b-container fluid>
        <b-row class="my-1">
            <b-col sm="5">
                <label>Name</label>
            </b-col>
            <b-col sm="5">
                <b-form-input placeholder="John Doe"></b-form-input>
            </b-col>
        </b-row>
        <b-row class="my-1">
            <b-col sm="5">
                <label>Number</label>
            </b-col>
            <b-col sm="5">
                <b-form-input placeholder="630-649-9483"></b-form-input>
            </b-col>
        </b-row>
        <b-row class="my-1">
            <b-col sm="5">
                <label>Email</label>
            </b-col>
            <b-col sm="5">
                <b-form-input placeholder="johndoe@gmail.com"></b-form-input>
            </b-col>
        </b-row>
        <b-row class="my-1">
            <b-col sm="5">
                <label>Address</label>
            </b-col>
            <b-col sm="5">
                <b-form-input placeholder="1029 Michigan Ave Chicago, IL 60616"></b-form-input>
            </b-col>
        </b-row>
    </b-container>

    <b-button variant="outline-primary" @click="$bvToast.show('save-confirm')">Save</b-button>
  </div>
</template>

<script>

export default {
  name: 'Profile',
  components: {
  },

  data() {
    return {
        
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

#profile_circle {
    width: 20vh;
    height: 20vh;
    margin: auto;
    display: flex;
    justify-content: center;
    align-items: center;
    background: whitesmoke;
    border-radius: 10rem;
    margin-bottom: 4rem;
    margin-top: 4rem;
    box-shadow: 0rem 0rem 0.2rem;
}

label {
    float: right;
}

.my-1 {
    margin-bottom: 2.25rem !important;
}

input {
    width: 50%;
}

@media screen and (max-width: 768px) {
    #profile_circle {
        width: 40vw;
        height: 40vw;
        margin: auto;
        display: flex;
        justify-content: center;
        align-items: center;
        background: whitesmoke;
        border-radius: 10rem;
        margin-bottom: 4rem;
        margin-top: 2rem;
        box-shadow: 0rem 0rem 0.2rem;
    }

    label {
        float: unset;
    }

    input {
        width: 100%;
    }
}




</style>
