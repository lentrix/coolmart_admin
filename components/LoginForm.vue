<template>
  <div class="row login-form">
    <div class="col-md-4">
      <div class="card">
        <div class="card-header bg-primary">
          <h4>Admin User Login</h4>
        </div>
        <div class="card-body">
          <form @submit.prevent="submit">
            <div class="form-group">
              <label for="user">User Name</label>
              <input
                required
                type="text"
                id="user"
                name="user"
                class="form-control">
            </div>
            <div class="form-group">
              <label for="password">Password</label>
              <input
                required
                type="password"
                id="password"
                name="password"
                class="form-control">
            </div>
            <div class="form-group">
              <button class="btn btn-primary float-right">
                User Login
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
    <div class="col-md-6 offset-md-2">
      <img src="https://securityintelligence.com/wp-content/uploads/2018/10/si-advanced-authentication-feature.jpg" alt="" class="authpic">
    </div>
  </div>
</template>

<script>

export default {
  data () {
    return {
      token: null,
    }
  },
  methods: {
    async submit (event) {
      const { user, password } = Object.fromEntries(new FormData(event.target))
      let response = await this.$axios.$post('http://localhost:8000/api/login',{
        user: user,
        password: password
      })
      console.log(response)
    },

  }
}
</script>

<style scoped>
  .login-form {
    margin-top: 20px;
  }
  .authpic {
    width: 100%;
  }
</style>
