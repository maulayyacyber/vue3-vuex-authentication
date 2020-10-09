<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-md-12">
        <div class="card border-0 shadow rounded">
          <div class="card-body">
            {{ isLoggedIn }}
            <hr>
            <button @click="logout" class="btn btn-primary btn-md">LOGOUT</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {

    computed: {
      isLoggedIn: function () {
        return this.$store.getters.isLoggedIn;
      }
    },

    methods: {
      logout: function () {
        this.$store.dispatch("LOGOUT").then(() => {
          this.$router.push("/");
        });
      }
    }

  }
</script>