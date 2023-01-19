<template>
  <div id="app">
    <h1 class="text-3xl font-bold underline">
      Студенти
    </h1>
    <table class="table-fixed">
      <thead>
        <tr>
          <th>Студент</th>
          <th>Здав/не здав</th>
          <th>Група</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in students" v-bind:key="item._id">
          <td>{{item.name}}</td>
          <td><input type="checkbox" v-model="item.isDonePr"></td>
          <td>{{item.group}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios'

export default ({
  data() {
    return {
      students: [],
      student: {"name": "", isDonePr: false, group: ""},
    }
  },
  mounted: function(){
    axios.get("http://34.82.81.113:3000/students").then((response) => {
      console.log(response.data);
      this.students = response.data;
    })
  },
  methods: {
    
  },
});
</script>

<style scoped>
</style>