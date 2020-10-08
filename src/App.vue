<template>
  <div id="app" class="small-container">
    <h1>Employee Details</h1>
     <employee-form />
    <employee-table :employee="employee" />
   

    <!-- Both the above and below does the same thing. v-bind is verbose but it also indicate that vue data binding -->
    <!-- <employee-table v-bind:employee="employee" /> -->
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import EmployeeTable from "./components/EmployeeTable.vue";
import EmployeeForm from "./components/EmployeeForm.vue";

export default {
  name: "App",
  components: {
    // HelloWorld
    EmployeeTable,
    EmployeeForm,
  },
  data() {
    return {
      employee: [
        {
          id: 1,
          name: "Jane Doe",
          email: "janedoe@xyx.com",
        },
        {
          id: 2,
          name: "Watson Shane",
          email: "watsonshane@xyz.com",
        },
      ],
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
