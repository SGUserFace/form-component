<template>
  <div>
    <my-form @add="add"
     :firstname="currentUser.firstname"
     :lastname="currentUser.lastname">
    </my-form>

      <table>
        <tr>
          <th>#</th>
          <th>First Name</th>
          <th>Last Name</th>
          <th>Actions</th>
        </tr>
        <tr v-for="user in users" :key="user.id">
          <td>{{ user.id }}</td>
          <td>{{ user.firstname }}</td>
          <td>{{ user.lastname }}</td>
          <td>
            <a @click.prevent="edit(user)" href="#">Edit</a>
          </td>
        </tr>
    </table>

  </div>
</template>

<script>
import MyForm from "@/components/MyForm";

export default {
  name: 'App',

  components: {
    MyForm
  },

  data() {
    return {
      currentUser: {
        id: null,
        firstname: null,
        lastname: null,
      },

      users: [
        { id: 1000, firstname: "Shai", lastname: "Gerbi", },
        { id: 2000, firstname: "Maya", lastname: "Cohen", },
      ],
    }
  },

  methods: {
    add(user) {
      console.log(`Add`);
      this.users.push(user);
    },
    edit(user) {
      this.currentUser = user;
    }
  }
}
</script>

<style scoped>
  table{
    border-collapse: collapse;
    font-family: Tahoma, fantasy;
  }

  table, th, td {
    border: 1px solid black;
    padding: 3px;
  }
</style>
