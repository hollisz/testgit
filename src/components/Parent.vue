<template>
  <div class="parent">
    <child v-bind:message="message2" v-bind:people="People"></child>
    <employee v-bind:Tasks="People"></employee>
  </div>
</template>

<script>
import Child from './Child'
import Employee from './Employee'
import Cell from './Cell'

export default {
  name: 'parent',
  props: {
    message2: String
  },
  data() {
    return {
      Jeremy: [
        { FileNumber: "MO-22-IGT-17-01", Task: 'SAS', Status: 'IT Manager', StartDate: '01/02/17', TestComplete: '01/03/17', EstHours: '8.00', actHours: '4.00' },
        { FileNumber: "MO-22-IGT-17-01", Task: 'Emulation', Status: 'IT Manager', StartDate: '01/02/17', TestComplete: '01/03/17', EstHours: '8.00', actHours: '4.00' },
        { FileNumber: "MO-22-IGT-17-01", Task: 'DTO', Status: 'IT Manager', StartDate: '01/02/17', TestComplete: '01/03/17', EstHours: '8.00', actHours: '4.00' }
      ],
      People: [
        { Name: "Jeremy Huddleston", Date: "7/1/2017", Type: "DTO", ScheduledHours: 0, BilledHours: 1 },
        { Name: "Jeremy Huddleston", Date: "7/2/2017", Type: "DTO", ScheduledHours: 4, BilledHours: 1 },
        { Name: "Jeremy Huddleston", Date: "7/3/2017", Type: "DTO", ScheduledHours: 3, BilledHours: 1 },
        { Name: "Jeremy Huddleston", Date: "7/4/2017", Type: "DTO", ScheduledHours: 4, BilledHours: 1 },
        { Name: "Jeremy Huddleston", Date: "7/5/2017", Type: "DTO", ScheduledHours: 5, BilledHours: 1 },
        { Name: "Albert Huddleston", Date: "7/5/2017", Type: "DTO", ScheduledHours: 6, BilledHours: 1 },
        { Name: "Jeremy Huddleston", Date: "7/10/2017", Type: "DTO", ScheduledHours: 1, BilledHours: 1 }
      ]
    }
  },
  methods: {


  },
  computed: {

  },
  components: {
    Child,
    Employee,
    Cell
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
</style>
