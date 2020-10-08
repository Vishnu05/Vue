
<template>
  <div id="employee-form">
    <form action="" @submit.prevent="handleSubmit">
      <label for="">Employee Name</label>
      <input  v-model="employee.name" type="text" name="" id="" />
      <label for="">Employee Email</label>
      <input v-model="employee.email" type="text" name="" id="" />
      <button>Add Employee</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "employee-form",
  data() {
    return {
      employee: {
        name: "",
        email: "",
      },
    };
  },
  methods: {
      handleSubmit() {
        console.log("Testing HandleSubmit")
        this.$$emit('add:employee', this.employee)
      }
  },
};
</script>

<style scoped>
form {
  margin-bottom: 2rem;
}
</style>