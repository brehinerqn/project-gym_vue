<template>


<div class="container-template">
    <nav>
      <!-- <router-link class="link" to="/Home">Home</router-link> -->
      <router-link class="link" to="/Principal">Principal</router-link>
      <router-link
        v-if="this.$route.path == '/Account'"
        class="link"
        to="/Account"
        >tu cuenta
      </router-link>
    </nav>
    <div id="login">
      <form>
        <div id="inp">
          <h3 id="title" style="text-align: center">Iniciar Sesion.</h3>

          <div class="form-group">
            <label for="exampleInputEmail1" style="color: aliceblue"
              >Email address</label
            >
            <input
              type="text"
              name="email"
              v-model="form.email"
              class="form-control"
              id="exampleInputEmail1"
              aria-describedby="emailHelp"
              placeholder="Enter email"
            />
            <span style="color: aliceblue" v-if="errors.email">{{
              errors.email[0]
            }}</span>
          </div>
          <div class="form-group">
            <label for="exampleInputPassword1" style="color: aliceblue"
              >Password</label
            >
            <input
              type="password"
              name="password"
              v-model="form.password"
              class="form-control"
              placeholder="Password"
            />
            <span style="color: aliceblue" v-if="errors.password">{{
              errors.password[0]
            }}</span>
          </div>
          <!-- <div class="form-group">
               <label for="exampleInputPassword1" style="color: aliceblue;">rol del usuario</label>
               <input type="roles_id" name="roles_id" v-model="form.roles_id" class="form-control"
                  placeholder="Rol">
               <span style="color:aliceblue;" v-if="errors.roles_id">{{ errors.roles_id[0] }}</span>

            </div> -->
          <p style="color: white" v-if="message">{{ message }}</p>
          <p style="color: white" v-if="message">{{ message }}</p>

          <br />
          <button
            class="btn btn-primary btn-lg active"
            aria-pressed="true"
            type="button"
            @click="login()"
          >
            entrar
          </button>
          <br />
          <br />

          <div id="link">
            <router-link class="link" to="/Register">registrarse</router-link>
            <router-link class="link" to="/forgot-password"
              >Olvidaste tu contraseña?</router-link
            >
          </div>
        </div>
      </form>

    </div>
  </div>





    <!-- <h1 style="font-feature-settings; width: 100vw; text-align: center;">
        Login
    </h1>
    <div>
        <form>
            <div>
                <label for="">Email</label>
                <input type="text" name="email" v-model="form.email" />
                <span v-if="errors.email">{{ errors.email[0] }}</span>
            </div>
            <br>

            <div>
                <label for="">Contraseña</label>
                <input type="password" name="password" v-model="form.password" />
                <span v-if="errors.password">{{ errors.password[0] }}</span>
            </div>
            <br>

            <div>
                <button @click="login()" type="button">Login</button>
            </div>
            <br>
            <router-link class="link" to="forgot-password">Olvidaste tu Contraseña</router-link>
            <p v-if="message">
                {{ message }}
            </p>
        </form>
    </div> -->
</template>
<style scoped>
@import "../assets/css/login.css";
</style>

<script>

export default {
    data() {
        return {
            message: null,
            form: {
                email: "",
                password: "",
            },
            errors: {},
        };
    },
    mounted() {
        if (this.$route.params.message)
            this.message = this.$route.params.message

    },

    methods: {
        async login() {
            try {
                const rs = await this.axios.post("/api/login", this.form);
                const role = rs.data.user.roles_id;

                switch (role) {
                    case 1:
                        this.$router.push({
                            path: "/Admin/Home",
                            // params: {
                            // token:rs.data.token,
                            // }
                        });
                        break;

                    case 2:
                        this.$router.push({
                            name: "Admin",
                        });
                        break;

                    case 3:
                        this.$router.push({
                            name: "Employe",
                        });
                        break;

                    case 4:
                        this.$router.push({
                            name: "Account",
                        });
                        break;

                    default:
                        this.$router.push({
                            name: "Login",
                        });
                        break;
                }

                localStorage.token = rs.data.token;
                localStorage.user = JSON.stringify(rs.data.user);
            } catch (e) {
                this.errors = {},
                this.message = null;

                if (e.response.data.errors)
                    this.errors = e.response.data.errors;
                    
                else (e.response.data.message)
                    this.message = e.response.data.message;


                console.log(e);
                this.errors = e.response.data.errors;
            }

        },
    },
};
</script>