
<template>
  <div id="employee-form">
    <form action="" @submit.prevent="handleSubmit">
      <label for="">Employee Name</label>
      <input
        ref="first"
        v-model="employee.name"
        type="text"
        :class="{ 'has-error': submitting && invalidName }"
        @focus="clearStatus"
        @keypress="clearStatus"
      />
      <label for="">Employee Email</label>
      <input
        v-model="employee.email"
        :class="{ 'has-error': submitting && invalidName }"
        type="text"
        @focus="clearStatus"
        @keypress="clearStatus"
      />

      <p v-if="error && submitting" class="error-message">
        ! Please fill out all the required fields
      </p>
      <p v-if="success" class="success-message">Employee added successfully</p>
      <button>Add Employee</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "employee-form",
  data() {
    return {
      submitting: false,
      error: false,
      success: false,
      employee: {
        name: "",
        email: "",
      },
    };
  },
  methods: {
    handleSubmit() {
      console.log("Testing HandleSubmit");

      this.submitting = true;
      this.clearStatus();

      if (this.invalidName || this.invalidEmail) {
        this.error = true;
        return;
      }

      this.$emit("add-employee", this.employee);
      // this.$refs.first.focus();
      this.employee = {
        name: "",
        email: "",
      };

      (this.error = false), (this.success = true);
      this.submitting = false;
    },
    clearStatus() {
      this.success = false;
      this.error = false;
    },
  },
  computed: {
    invalidName() {
      return this.employee.name === "";
    },
    invalidEmail() {
      return this.employee.email === "";
    },
  },
};
</script>

<style scoped>
form {
  margin-bottom: 2rem;
}

[class*="-message"] {
  font-weight: 500;
}
.error-message {
  color: #d33c40;
}

.success-message {
  color: #32a95d;
}
</style>