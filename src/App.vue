<template>
  <div id="app">
    <router-view/>
    <transition name="fade">
      <div v-if="$route.name != 'Home'" id="nav">
        <div id="nav_content">
          <router-link to="/calendar">
            <div class="nav_icon">
              <b-icon icon="calendar" scale="1" aria-hidden="true"></b-icon>
              <p>Calendar</p>
            </div>
          </router-link>
          <router-link to="/messages">
            <div class="nav_icon">
              <b-icon icon="chat" scale="1" aria-hidden="true"></b-icon>
              <p>Messages</p>
            </div>
          </router-link>
          <router-link to="/todo">
            <div class="nav_icon">
              <b-icon icon="card-checklist" scale="1" aria-hidden="true"></b-icon>
              <p>To-Do</p>
            </div>
          </router-link>
          <router-link to="/listings">
            <div class="nav_icon">
              <b-icon icon="list-ul" scale="1" aria-hidden="true"></b-icon>
              <p>Job Listings</p>
            </div>
          </router-link>
          <router-link to="/profile">
            <div class="nav_icon">
              <b-icon icon="person" scale="1" aria-hidden="true"></b-icon>
              <p>Profile</p>
            </div>
          </router-link>
        </div>
      </div>
    </transition>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  bottom: 0;
  position: fixed;
  margin: auto;
  width: -webkit-fill-available;
  padding-bottom: 0;
  background: linear-gradient(120deg, rgba(241,43,17, 0.7), rgba(245,173,25, 0.7));
  box-shadow: 1rem 1rem 2rem black;
  z-index: 1000;
}

#nav a {
  font-weight: bold;
  transition: 0.4s;
  color: black;
  margin-right: 1rem;
  margin-left: 1rem;
}

#nav a.router-link-exact-active {
  color: whitesmoke;
}

#nav_content {
  display: inline-flex;
}

.nav_icon {
  margin: 1rem;
}

body{
  margin: 0;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}


@media screen and (max-width: 768px) {
  .nav_icon {
    margin: 0;
  }

  .nav_icon p {
    font-size: 0.6rem;
  }

  #nav a {
    margin-top: 1rem;
  }
}
</style>
