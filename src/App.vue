<template>
  <div id="app">
    <parent message2=message3 rows4=rowvals></parent>
  </div>
</template>

<script>
import Parent from './components/Parent'

var emps = {"rows":[ 
  { id: 1, name: "Chandler Bing", phone: '305-917-1301', profession: 'IT Manager' },
  { id: 2, name: "Ross Geller", phone: '210-684-8953', profession: 'Paleontologist' },
  { id: 3, name: "Rachel Green", phone: '765-338-0312', profession: 'Waitress' },
  { id: 4, name: "Monica Geller", phone: '714-541-3336', profession: 'Head Chef' },
  { id: 5, name: "Joey Tribbiani", phone: '972-297-6037', profession: 'Actor' },
  { id: 6, name: "Phoebe Buffay", phone: '760-318-8376', profession: 'Masseuse' }
]}

export default {
  name: 'app',
  data() {
    return {
      message3: "Hello",
      items2: [
        { text: 'Learn JavaScript' },
        { text: 'Learn Vue' },
        { text: 'Build something awesome' }
      ]
    }
  },
  computed: {
    "rowvals": {
      get: function () {
        var obj = JSON.parse(emps);
        return obj;
      }
    }
  },
  components: {
    Parent
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
