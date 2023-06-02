<template>
  <div id="app">
    <DatePicker
      v-model="selectDate"
      :disabled="false"
    />
    <div
      v-for="i in selectDate"
      :key="i"
      class="detail-item"
    >
      <span class="item-label fl">{{i}}：</span>
    </div>
  </div>
</template>

<script>
// import DatePicker from './components/DatePicker.vue'
import DatePicker from '../dist/datepicker.min.js'
// import DatePicker from 'sta-datepicker'
export default {
  name: 'app',
  components: {
    DatePicker
  },
  data() {
    return {
      selectDate: ['2023/05/31']
    }
  },
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
