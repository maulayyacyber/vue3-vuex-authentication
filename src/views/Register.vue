<template>
    <div class="container mt-5">
        <div class="row justify-content-center">
            <div class="col-md-4">
                <div class="card border-0 shadow rounded">
                    <div class="card-body">
                        <div>
                            <div class="form-group">
                                <label>Full Name</label>
                                <input type="text" v-model="name" class="form-control">
                            </div>
                            <div class="form-group">
                                <label>Email address</label>
                                <input type="email" v-model="email" class="form-control">
                            </div>
                            <div class="form-group">
                                <label>Password</label>
                                <input type="password" v-model="password" class="form-control">
                            </div>
                            <button @click.prevent="register" class="btn btn-primary btn-block">REGISTER</button>
                        </div>
                    </div>
                </div>
                <div class="register mt-3 text-center">
                    <p>Sudah punya akun ? <router-link :to="{name: 'Login'}">Login Disini!</router-link></p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {

        data() {
            return {
                name: '',
                email: '',
                password: ''
            }
        },

        methods: {
            register() {
                let name     = this.name
                let email    = this.email
                let password = this.password
                this.$store
                    .dispatch("REGISTER", {
                        name,
                        email,
                        password
                    })
                    .then(() => this.$router.push("/dashboard"))
                    .catch(err => console.log(err))
            }
        }

    }
</script>