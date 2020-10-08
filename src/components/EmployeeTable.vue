
<template>
  <div id="employee-table">
    <table>
      <thead>
        <tr>
          <th>Employee Name</th>
          <th>Employee Email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="emp in employee" :key="emp.id" >
            <td>{{emp.name}}</td>
            <td>{{emp.email}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
    name: 'employee-table',
    props: {
        employee: Array
    }
};

</script>

<style  scoped>

</style>