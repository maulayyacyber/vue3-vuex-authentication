<template>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-md-4">
        <div class="card border-0 shadow rounded">
          <div class="card-body">
            <div>
              <div class="form-group">
                <label>Email address</label>
                <input type="email" v-model="email" class="form-control">
              </div>
              <div class="form-group">
                <label>Password</label>
                <input type="password" v-model="password" class="form-control">
              </div>
              <div class="form-group form-check">
                <input type="checkbox" class="form-check-input" id="exampleCheck1">
                <label class="form-check-label" for="exampleCheck1">Ingatkan Saya</label>
              </div>
              <button @click.prevent="login" class="btn btn-primary btn-block">LOGIN</button>
            </div>
          </div>
        </div>
        <div class="register mt-3 text-center">
          <p>Belum punya akun ? <router-link :to="{name: 'Register'}">Daftar Sekarang!</router-link></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {

    data() {
      return {
        email: '',
        password: ''
      }
    },

    methods: {
      login() {
        let email    = this.email
        let password = this.password
        this.$store
          .dispatch("LOGIN", {
            email,
            password
          })
          .then(() => this.$router.push("/dashboard"))
          .catch(err => console.log(err))
      }
    }

  }
</script>