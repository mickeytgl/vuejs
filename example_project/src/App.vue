<template>
  <div id="main-app">
      <h1>{{title}}</h1>
        <ul class="appointment-list" v-for="(item, i) in appointments" :key="i">
          <li>{{item.petName}}</li>
        </ul>
  </div>
</template>

<script>
  export default {
    name: 'MainApp',
    data() {
      return {
        title: 'Appointment',
        theAppointments: []        
      }; //return
    }, //data
    created: function() {
      $.getJSON('./build/appointments.json')
      .done( info => {
        this.theAppointments = info;
      });//getJSON
    } //created
  }; //default

</script>

<style scoped>
  .appointment-list {
    margin: 0;
    padding: 0;
    list-style-type: none;
    margin: 10px 5%;
    font-size: 1.7 rem;
  }
</style>