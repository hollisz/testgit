<template>
  <div class="employee">
    <div class="container">
      <div class="panel panel-primary">
        <div class="panel-heading">
          <div class="row">
            <div class="col-md-3">
              <h4>Jeremy Huddleston</h4>
            </div>
            <div class="col-md-5">
              <h5>Total Hours: 20.75 Minus OH: 18</h5>
            </div>
          </div>
        </div>
        <div class="table-responsive">
          <table class="table table-bordered table-fit">
            <thead>
              <tr bgcolor="#bgbgbg">
                <th></th>
                <th v-for="col in columns" v-bind:item="col">{{col}}</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="row in Tasks" v-bind:item="row">
                <td><input id="checkBox" type="checkbox"></td>
                <td v-for="col in columns" v-bind:item="col">{{row[col]}}</td>
              </tr>
            </tbody>
          </table>
          <div id="context" @contextmenu.prevent="handler('context', $event)">r-clickasdfsdfd</div>
          <div class="text-center">
            <button type="button" class="btn btn-primary" v-on:click="deleteItem">Re-Assign</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'employee',
  props: {
    Name: String,
    Tasks: Array
  },
  data() {
    return {

    }
  },
  methods: {
    "deleteItem": function deleteItem() {
      console.log("Clicked");
      this.Tasks.splice(0, 1);
    },
    "handler": function handler(control, e) {
      console.log("Right clik");
      var posx = e.clientX + window.pageXOffset + 'px'; //Left Position of Mouse Pointer
      var posy = e.clientY + window.pageYOffset + 'px'; //Top Position of Mouse Pointer
      document.getElementById(control).style.position = 'absolute';
      document.getElementById(control).style.display = 'inline';
      document.getElementById(control).style.left = posx;
      document.getElementById(control).style.top = posy;
    }
  },
  computed: {
    "columns": function columns() {
      var arr = this.Tasks;
      //arr.splice(0,1);

      if (this.Tasks.length == 0) {
        return [];
      }
      return Object.keys(this.Tasks[0])
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import 'https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css';

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

.ContextItem <!-Context Menu Item Style--> {
  background-color: White;
  color: Black;
  font-weight: normal;
}

.ContextItem:hover <!-Context Menu Item Style On Mouse Over--> {
  background-color: #0066FF;
  color: White;
  font-weight: bold;
}

.detailItem {
  background: transparant;
}

.detailItem:hover {
  background-color: #FEE378;
  border: 1px outset #222222;
  font-weight: bold;
  cursor: default;
}
</style>
