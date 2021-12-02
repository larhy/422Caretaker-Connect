<template>
  <div class="jobs">
    <b-form-group id="view_select"
      v-slot="{ ariaDescribedby }"
    >
        <b-form-radio-group
            id="btn-radios-2"
            v-model="selected"
            :options="options"
            :aria-describedby="ariaDescribedby"
            button-variant="outline-primary"
            name="radio-btn-outline"
            buttons
        ></b-form-radio-group>
    </b-form-group>
    <div id="content">
        <transition name="fade">
            <div v-if="selected == 'jobs'">
                <b-list-group>
                    <b-list-group-item button v-for="(job, index) in jobs" :key="index">
                        <div>
                            <b-row class="my-1">
                                <b-col sm="3">
                                    <div id="profile_circle">
                                        <b-icon icon="person" scale="3" aria-hidden="true"></b-icon>
                                    </div>
                                    <div>
                                        <p>{{job.name}}</p>
                                        <div class="job_type">{{job.type}}</div>
                                    </div>
                                </b-col>
                                <b-col sm="6">
                                    <div id="details" style="display: inline-grid; margin-top: 2rem">
                                        <div style="display: inline-flex">
                                            <p style="font-weight: bold; margin-right: 1rem;">Location: </p>
                                            <p>{{job.location}}</p>
                                        </div>

                                        <div style="display: inline-flex">
                                            <p style="font-weight: bold; margin-right: 1rem;">Time: </p>
                                            <p>{{job.time}}</p>
                                        </div>

                                        <div v-if="job.type == 'Parent'" style="display: inline-flex">
                                            <p style="font-weight: bold; margin-right: 1rem;">Kids: </p>
                                            <p>{{job.kids}}</p>
                                        </div>

                                        <div style="display: inline-flex">
                                            <p style="font-weight: bold; margin-right: 1rem;">Salary: </p>
                                            <p>${{job.salary}}/hr</p>
                                        </div>
                                    </div>
                                </b-col>
                                <b-col sm="3" style="margin-top: 0">
                                    <b-row class="my-1">
                                        <div class="posted_at">
                                            <p style="font-weight: bold; margin-right: 1rem;">Posted </p>
                                            <p>{{job.posted_at}}</p>
                                        </div>
                                    </b-row>
                                    <b-button class="card_btn" variant="outline-success">Request</b-button>
                                </b-col>
                            </b-row>
                        </div>
                    </b-list-group-item>
                </b-list-group>
            </div>
        </transition>

        <transition name="fade">
            <div v-if="selected == 'requests'">
                <b-list-group>
                    <b-list-group-item button v-for="(job, index) in requests" :key="index">
                        <div>
                            <b-row class="my-1">
                                <b-col sm="3">
                                    <div id="profile_circle">
                                        <b-icon icon="person" scale="3" aria-hidden="true"></b-icon>
                                    </div>
                                    <div>
                                        <p>{{job.name}}</p>
                                        <div class="job_type">{{job.type}}</div>
                                    </div>
                                </b-col>
                                <b-col sm="6">
                                    <div id="details" style="display: inline-grid; margin-top: 2rem">
                                        <div style="display: inline-flex">
                                            <p style="font-weight: bold; margin-right: 1rem;">Location: </p>
                                            <p>{{job.location}}</p>
                                        </div>

                                        <div style="display: inline-flex">
                                            <p style="font-weight: bold; margin-right: 1rem;">Time: </p>
                                            <p>{{job.time}}</p>
                                        </div>

                                        <div v-if="job.type == 'Parent'" style="display: inline-flex">
                                            <p style="font-weight: bold; margin-right: 1rem;">Kids: </p>
                                            <p>{{job.kids}}</p>
                                        </div>

                                        <div style="display: inline-flex">
                                            <p style="font-weight: bold; margin-right: 1rem;">Salary: </p>
                                            <p>${{job.salary}}/hr</p>
                                        </div>
                                    </div>
                                </b-col>
                                <b-col sm="3" style="margin-top: 0">
                                    <b-row class="my-1">
                                        <div class="posted_at">
                                            <p style="font-weight: bold; margin-right: 1rem;">Posted </p>
                                            <p>{{job.posted_at}}</p>
                                        </div>
                                    </b-row>
                                    <div class="card_btn2">
                                        <b-button variant="outline-success" style="margin-right: 1rem" @click="requestClick">Accept</b-button>
                                        <b-button variant="outline-danger" @click="requestClick">Decline</b-button>
                                    </div>
                                </b-col>
                            </b-row>
                        </div>
                    </b-list-group-item>
                </b-list-group>
            </div>
        </transition>

        <transition name="fade">
            <div id="create_form" v-if="selected == 'create'">
                <div id="time_select" style="display: inline-grid">
                    <label style="font-weight: bold">Days and Times</label>
                    <div id="timepickers">
                        <div class="timepick" v-for="day in ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday']" :key="day">
                            <label style="font-weight: bold">{{day}}</label>
                            <b-row class="my-1">
                                <b-col sm="2">
                                    <label>Start</label>
                                </b-col>
                                <b-col sm="8">
                                    <b-form-timepicker locale="en"></b-form-timepicker>
                                </b-col>
                            </b-row>
                            <b-row class="my-1">
                                <b-col sm="2">
                                    <label>End</label>
                                </b-col>
                                <b-col sm="8">
                                    <b-form-timepicker locale="en"></b-form-timepicker>
                                </b-col>
                            </b-row>
                            
                        </div>
                    </div>
                </div>
                <div style="margin-top: 3rem">
                    <b-row class="my-1">
                        <b-col sm="5">
                            <label style="font-weight: bold">Salary</label>
                        </b-col>
                        <b-col sm="5">
                            <b-form-input type="number"></b-form-input>
                        </b-col>
                    </b-row>
                </div>
                <div style="margin-top: 3rem">
                    <b-row class="my-1">
                        <b-col sm="5">
                            <label style="font-weight: bold">Number of kids</label>
                        </b-col>
                        <b-col sm="5">
                            <b-form-input type="number"></b-form-input>
                        </b-col>
                    </b-row>
                </div>
                <div style="margin-top: 3rem">
                    <b-row class="my-1">
                        <b-col sm="5">
                            <label style="font-weight: bold">Address</label>
                        </b-col>
                        <b-col sm="5">
                            <b-form-input></b-form-input>
                        </b-col>
                    </b-row>
                </div>
                <div style="margin-top: 3rem">
                    <b-row class="my-1">
                        <b-col sm="5">
                            <label style="font-weight: bold">Tasks</label>
                        </b-col>
                        <b-col sm="5">
                            <b-form-input></b-form-input>
                        </b-col>
                    </b-row>
                </div>
                <b-button class="create_btn" variant="outline-success">Create</b-button>
            </div>
        </transition>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Jobs',
  components: {
  },

  data() {
    return {
        time_selected: [],
        time_options: [{'text': "Sunday", value: "sun"}, {'text': "Monday", value: "monday"}, {'text': "Tuesday", value: "tues"}, {'text': "Wednesday", value: "wed"}, {'text': "Thursday", value: "thurs"}, {'text': "Friday", value: "fri"}, {'text': "Saturday", value: "sat"}],
        selected: "jobs",
        options: [{text: "Jobs", value: "jobs"}, {text: "Requests (1)", value: "requests"}, {text: "Create Job", value: "create"}],
        requests: [
            {
                "name": "Lily Collins",
                "salary": 18,
                "location": "Chicago, IL",
                "time": "Mon, Wed: 8am-6pm",
                "kids": 1,
                "posted_at": "11/28/2021",
                "type": "Parent"
            },
        ],
        jobs: [
                {
                    "name": "Jack Robinson",
                    "salary": 20,
                    "location": "Chicago, IL",
                    "time": "Mon, Wed, Fri: 9am-5pm | Tues, Thurs: 12pm-4pm",
                    "kids": 3,
                    "posted_at": "11/10/2021",
                    "type": "Parent"
                },
                {
                    "name": "Lily Collins",
                    "salary": 18,
                    "location": "Chicago, IL",
                    "time": "Mon, Wed: 8am-6pm",
                    "kids": 1,
                    "posted_at": "11/28/2021",
                    "type": "Parent"
                },
                {
                    "name": "Samuel Jacob",
                    "salary": 17,
                    "location": "Chicago, IL",
                    "time": "Mon, Tues, Wed, Thurs, Fri: 9am-6pm",
                    "posted_at": "10/01/2021",
                    "type": "Babysitter"
                },
                {
                    "name": "Lily Collins",
                    "salary": 18,
                    "location": "Chicago, IL",
                    "time": "Mon, Wed: 8am-6pm",
                    "kids": 1,
                    "posted_at": "11/28/2021",
                    "type": "Parent"
                },
                {
                    "name": "Lily Collins",
                    "salary": 18,
                    "location": "Chicago, IL",
                    "time": "Mon, Wed: 8am-6pm",
                    "kids": 1,
                    "posted_at": "11/28/2021",
                    "type": "Parent"
                },
                {
                    "name": "Lily Collins",
                    "salary": 18,
                    "location": "Chicago, IL",
                    "time": "Mon, Wed: 8am-6pm",
                    "kids": 1,
                    "posted_at": "11/28/2021",
                    "type": "Parent"
                },
                {
                    "name": "Lily Collins",
                    "salary": 18,
                    "location": "Chicago, IL",
                    "time": "Mon, Wed: 8am-6pm",
                    "kids": 1,
                    "posted_at": "11/28/2021",
                    "type": "Parent"
                },
                {
                    "name": "Lily Collins",
                    "salary": 18,
                    "location": "Chicago, IL",
                    "time": "Mon, Wed: 8am-6pm",
                    "kids": 1,
                    "posted_at": "11/28/2021",
                    "type": "Parent"
                },
        ]
    }
  },

  methods: {
    requestClick: function () {
      this.requests = []
      this.options[1].text = "Requests"
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

#btn-radios-2 {
    margin-top: 2rem;
}

#content {
    width: 80vw;
    top: 10vh;
    position: relative;
    margin: auto;
    margin-bottom: 20vh;
}

#create_form {
    width: 80vw;
    margin: auto;
    background: whitesmoke;
    min-height: 50vh;
    border-radius: 3rem;
    padding-top: 2rem;
    box-shadow: 0rem 0rem 2rem rgb(10 10 10 / 20%);
}

#profile_circle {
    width: 10vh;
    height: 10vh;
    margin: auto;
    display: flex;
    justify-content: center;
    align-items: center;
    background: whitesmoke;
    border-radius: 10rem;
    margin-bottom: 1rem;
    box-shadow: 0rem 0rem 0.2rem;
}

.job_type {
    margin-left: 0.4rem;
    background: cornflowerblue;
    color: white;
    border-radius: 0.7rem;
    padding: 0.5rem;
    width: 15%;
    margin: auto;
    font-size: 0.7rem;
}

.col-sm-3 {
    margin-top: 2rem;
    margin-bottom: 2rem;
}

.posted_at {
    display: inline-flex; float: right; margin-right: 2rem; opacity: 0.6; position: absolute; left: 0;
}

.card_btn {
    position: absolute; right: 2rem; bottom: 2rem;
}

.card_btn2 {
    display: inline-flex; position: absolute; right: 2rem; bottom: 2rem;
}

#timepickers {
    display: inline-flex; 
    margin-top: 2rem;
}

.create_btn {
    margin-top: 5rem
}

@media screen and (min-width: 768px) {
    #view_select {
        float: left;
        margin-left: 2rem;
        position: absolute;
        top: 0;
    }
}

@media screen and (max-width: 768px) {
    .job_type {
        margin-left: 0.4rem;
        background: cornflowerblue;
        color: white;
        border-radius: 0.7rem;
        padding: 0.5rem;
        margin: auto;
        font-size: 0.7rem;
        width: 25%;
    }

    #details {
        display: grid !important;
    }

    #timepickers {
        display: block;
        margin-top: 2rem;
    }

    #timepickers .timepick {
        margin-bottom: 2rem;
    }

    .create_btn {
        margin-top: 4rem;
        margin-bottom: 1rem;
    }

    .col-sm-5 input {
        width: 80%;
        margin: auto;
    }

    .posted_at {
        display: inline-flex; float: unset; margin-right: unset; opacity: 0.6; position: unset; left: unset;
    }

    .card_btn {
        position: unset; right: unset; bottom: unset;
    }

    .card_btn2 {
        display: block; position: unset; right: unset; bottom: unset;
    }
}

</style>

<style>
#btn-radios-2 input {
    opacity: 0 !important;
}
</style>
