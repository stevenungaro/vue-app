<template>
  <div id="app" class="small-container">
    <!-- <img
      id="logo"
      alt="Vue logo"
      src="https://cdn11.bigcommerce.com/s-balh3740/images/stencil/1280x1280/products/11560/3716/steve_irwin__80879.1572784062.jpg?c=2"
    /> -->
    <HelloWorld msg="Welcome to Steve Land.js App" />
    <h1>Employees</h1>
    <employee-form @add:employee="addEmployee" />
    <employee-table :employees="employees" @delete:employee="deleteEmployee" @edit:employee="editEmployee" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import EmployeeTable from "@/components/EmployeeTable.vue";
import EmployeeForm from "@/components/EmployeeForm.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
    EmployeeTable,
    EmployeeForm,
  },
  data() {
    return {
      employees: [
        {
          id: 1,
          name: "Richard Hendricks",
          email: "richard@piedpiper.com",
        },
        {
          id: 2,
          name: "Bertram Gilfoyle",
          email: "gilfoyle@piedpiper.com",
        },
        {
          id: 3,
          name: "Dinesh Chugtai",
          email: "dinesh@piedpiper.com",
        },
      ],
    };
  },
  methods: {
    addEmployee(employee) {
      const lastId = this.employees.length > 0 ? this.employees[this.employees.length - 1].id : 0;
      const id = lastId + 1;
      const newEmployee = { ...employee, id };
      this.employees = [...this.employees, newEmployee];
    },
    deleteEmployee(id) {
      this.employees = this.employees.filter((employee) => employee.id !== id);
    },
    editEmployee(id, updatedEmployee) {
      this.employees = this.employees.map((employee) => (employee.id === id ? updatedEmployee : employee));
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
button {
  background: #009435;
  border: 1px solid #009435;
}

.small-container {
  max-width: 680px;
}

#logo {
  width: 256px;
}
</style>
