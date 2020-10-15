
<template>
  <div id="employee-table">
    <p v-if="employee.length < 1" class="empty-table">No Employees</p>
    <table>
      <thead>
        <tr>
          <th>Employee Name</th>
          <th>Employee Email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="emp in employee" :key="emp.id">
          <td v-if="editing === emp.id">
            <input type="text" v-model="emp.name" />
          </td>
          <td v-else>{{ emp.name }}</td>

          <td v-if="editing === emp.id">
            <input type="text" v-model="emp.email" />
          </td>
          <td v-else>{{ emp.email }}</td>

          <td v-if="editing === emp.id">
            <button @click="editEmployee(employee)">Save</button>
            <button class="muted-button" @click="editing = null">Cancel</button>
          </td>
          <td v-else>
            <button @click="editMode(emp.id)">Edit</button>
            <button @click="$emit('delete-employee', emp.id)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "employee-table",
  props: {
    employee: Array,
  },
  data() {
    return {
      editing: null,
    };
  },
  methods: {
    editMode(id) {
      this.editing = id;
    },

    editEmployee(employee) {
      if (employee.name === "" || employee.email === "") return;
      this.$emit("edit-employee", employee.id, employee);
      this.editing = null;
    },
  },
};
</script>

<style  scoped>
button {
  margin: 0 0.5rem 0 0;
}

#empty-table {
  color: red;
}
</style> 