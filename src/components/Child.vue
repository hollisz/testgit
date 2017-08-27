
<template>
  <div class="child">
    <div class="container">
      <div class="DivToScroll">
        <div class="DivWithScroll">
          <div class="row">
            <div class="text-right">
              <p>
                <a class="btn btn-primary" data-toggle="collapse" href="#collapseExample" aria-expanded="false" aria-controls="collapseExample">
                  <span class="glyphicon glyphicon-chevron-down"></span> Region <br>
                </a>
              </p>
            </div>
            <div class="col-md-12">
              <div class="table-responsive">
                <table class="table table-bordered">
                  <thead>
                    <tr>
                      <td>July 2017</td>
                      <td v-for="col in Dates" v-bind:item="col">{{ col }}</td>
                    </tr>
                    <tr bgcolor="#b3d9ff">
                      <th></th>
                      <td v-for="col in Days" v-bind:item="col">{{ col }}</td>
                    </tr>
                    <tr>
                      <th bgcolor="#00FF00">Engineering Resources</th>
                      <td v-for="col in Days"></td>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="row in test" v-bind:item="row">
                      <td>{{ row.Name }}</td>
                      <td v-for="day in row.Days" :class="day.Class">
                        {{ day.Hours }}
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Cell from './Cell'

export default {
  name: 'child',
  props: {
    message: String,
    people: Array
  },
  data() {
    return {
      Dates: ["1", "2", "3", "4", "5", "6", "7", "8", "9", "10"],
      Days: ["S", "S", "M", "T", "W", "T", "F", "S", "S", "M"],
      blueActive: true,
      dtoActive: true,
      classObject: {
        blueActive: true
      }
    }
  },
  methods: {
    "sumscheduled": function sumscheduled() {
      var sum = 0;
      var i = 0;

      for (; this.people[i];) {
        sum = sum + this.people[i].ScheduledHours;
        i++;
      }

      return sum;
    },
    "compare": function compare(a, b) {
      if (a.Name < b.Name)
        return -1;
      if (a.Name > b.Name)
        return 1;
      return 0;
    },
    "sortPeople": function sortPeople() {
      var arr = this.people;
      arr.sort(this.compare);

      return arr;
    }
  },
  computed: {
    "test": function test() {
      var scheduled = 0;
      var billed = 0;
      var hours = 0;
      var i = 0;
      var len = 0;
      var IDs = new Object();
      var person = 0;

      var array = this.sortPeople();
      var name = array[0].Name;
      len = array.length - 1;

      while (i < len) {
        name = array[i].Name;
        IDs[person] = { Name: array[i].Name, Days: [] };
        while ((array[i].Name == name) && (i < len)) {
          scheduled = scheduled + array[i].ScheduledHours;
          billed = billed + array[i].BilledHours;
          hours = billed + scheduled;
          console.log(i + array[i].Name + " " + scheduled + " " + billed);
          i++;
          if (hours >= 8 || !(i < len) || array[i].Name != name) {
            console.info(JSON.stringify(IDs, null, '  '))
            IDs[person].Days.push({ Hours: (hours), Class: "Dto" });
            hours = 0;
            billed = 0;
            scheduled = 0;
            console.info(JSON.stringify(IDs, null, '  '))
          }
        }
        person++;

      }

      return IDs;
    },
    "columns": function columns() {
      if (this.people.length == 0) {
        return [];
      }
      return Object.keys(this.people[0])
    }
  },
  components: {
    Cell,
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import 'https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css';

.dates {
  color: #cce6ff
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

.blue {
  color: navy
}

.Dto {
  background-color: hotpink;
}
</style>
