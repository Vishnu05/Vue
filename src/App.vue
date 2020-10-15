<template>
  <div id="app" class="small-container">
    <h1>Employee Details</h1>

    <!-- Components name should be declared in kebab case -->
    <employee-form @add-employee="addEmployee" />
    <employee-table
      :employee="employee"
      @delete-employee="deleteEmployee"
      @edit-employee="editEmployee"
    />

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

  // in components we have declare all the components which is used in the application. Helps to identify
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
  methods: {
    // while adding employee, primary id is not defined need to check on that
    addEmployee(employee) {
      this.employee = [...this.employee, employee];
      const lastId =
        this.employee.length > 0
          ? this.employee[this.employee.length - 1].id
          : 0;
      console.log("lastid value is ", lastId);
      const id = lastId + 1;
      const newEmployee = { ...employee, id };
      console.log("new employee values are ", newEmployee);
      this.employee = [...this.employee, newEmployee];
    },

    deleteEmployee(id) {
      this.employee = this.employee.filter((employee) => employee.id !== id);
    },

    editEmployee(id, updatedEmployee) {
      this.employee = this.employee.map((employee) =>
        employee.id === id ? updatedEmployee : employee
      );
    },
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
