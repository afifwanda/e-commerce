<template>
<div>
  <AdminNavbar></AdminNavbar>
  <div class="register">
   <h3> Register </h3>
        <form id="form-signUp" action="" method="POST">
            <label for="fname">Name:</label><br>
            <input type="text" id="Name" name="Name" value="" v-model="name" required><br>
            <label for="fname">Email:</label><br>
            <input type="text" id="email" name="email" value="" v-model="email" required><br>
            <label for="lname">Password:</label><br>
            <input type="password" name="password" value="" v-model="password" required><br><br>
            <input type="submit" class="btn btn-dark" value="Submit" v-on:click.prevent="register">
        </form>
  </div>
</div>
</template>
<script>
import axios from 'axios';
import AdminNavbar from '../components/AdminNavbar.vue';

export default {
  name: 'Register',
  data() {
    return {
      baseUrl: 'https://pure-plains-87911.herokuapp.com',
      name: '',
      email: '',
      password: '',
      roles: 'admin',
    };
  },
  components: {
    AdminNavbar,
  },
  created() {

  },
  methods: {
    register() {
      axios({
        method: 'POST',
        url: `${this.baseUrl}/admin/register`,
        data: {
          name: this.name,
          email: this.email,
          password: this.password,
          roles: this.roles,
        },
      })
        .then((data) => {
          console.log(data);
          this.$router.push({ name: 'Login' });
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>
<style scoped>
.register {
  border-color: black;
  border-style : double;
  width: 20%;
  text-align: center;
  font-family: "Lato";
  margin : 100px auto;
  background: white;
  padding: 15px;
}
</style>
