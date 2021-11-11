<template>
  <div class="home">
    <transition name="fade">
      <div id="login" v-if="loggedIn != true">
        <div id="home_title">Caretaker Connect</div>
        <div id="login">
          <b-form-input style="margin-bottom: 2rem" v-model="username" placeholder="username"></b-form-input>
          <b-form-input v-model="pw" type="password" style="margin-bottom: 2rem" placeholder="password"></b-form-input>
          <b-button variant="outline-secondary" @click="loggedIn = true">Login</b-button>
        </div>
      </div>
    </transition>

    <transition name="fade2">
      <div id="home_view" v-if="loggedIn == true">
        <div class="icon_row">
          <router-link to="/calendar">
            <div class="h_nav_icon" style="float: left">
              <b-icon icon="calendar" :scale="iconScale" aria-hidden="true"></b-icon>
              <p>Calendar</p>
            </div>
          </router-link>

          <router-link to="/messages">
            <div class="h_nav_icon" style="float: right">
              <b-icon icon="chat" :scale="iconScale" aria-hidden="true"></b-icon>
              <p>Messages</p>
            </div>
          </router-link>
        </div>

        <div class="icon_row">
          <router-link to="/todo">
            <div class="h_nav_icon" style="float: left">
              <b-icon icon="card-checklist" :scale="iconScale" aria-hidden="true"></b-icon>
              <p>To-Do</p>
            </div>
          </router-link>

          <router-link to="/listings">
            <div class="h_nav_icon" style="float: right">
              <b-icon icon="list-ul" :scale="iconScale" aria-hidden="true"></b-icon>
              <p>Job Listings</p>
            </div>
          </router-link>
        </div>

        <div>
          <router-link to="/profile">
            <div class="h_nav_icon">
              <b-icon icon="person" :scale="iconScale" aria-hidden="true"></b-icon>
              <p>Profile</p>
            </div>
          </router-link>
        </div>
        <div id="menu_title">Main Menu</div>
      </div>
    </transition>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  data() {
    return {
      username: "",
      pw: "",
      loggedIn: false,
      iconScale: "3"
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

#home_title {
  font-family: pumpkin;
  font-size: 4rem;
  padding: 4rem;
  padding-top: 10%;
  margin-top: 0;
  color: white;
}

#menu_title {
  font-family: pumpkin;
  font-size: 4rem;
  padding: 4rem;
  padding-top: 20%;
  margin-top: 0;
  color: white;
}

.home {
  position: relative;
  background: linear-gradient(120deg, #F12711, #F5AF19);
  min-height: 100vh;
  min-width: 100vw;
}

#login {
  width: 30%;
  margin: auto;
}

.btn-outline-secondary {
    color: white;
    border-color: white;
}

.h_nav_icon {
  position: relative;
  color: lightgray;
  transition: 0.4s;
  cursor: pointer;
}

.h_nav_icon:hover {
  color: white;
}

.icon_row {
  width: 26vw;
  margin: 5rem;
}

#home_view {
  display: inline-grid;
  margin: auto;
  margin-top: 10rem;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

.fade2-enter-active, .fade2-leave-active {
  transition: opacity .5s;
  transition-delay: 800ms;
}
.fade2-enter, .fade2-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

.h_nav_icon p {
  margin-top: 4rem;
}

@media screen and (max-width: 768px) {
  #login {
    width: 90%;
  }

  #home_view {
    margin-top: 4rem;
  }

  .icon_row {
    width: unset;
    margin: 3rem;
  }

  .h_nav_icon p {
    margin-top: 1rem;
  }
}

</style>
