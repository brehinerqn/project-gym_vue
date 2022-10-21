<template>
    <h1 style="font-style: oblique; width: 100vw; text-align: center;">
       Registro
    </h1>

    <div style="font-feature-settings; width: 100vw; text-align: center;">
        <form>
             <div>
                <label for="">Nombre</label><br>
                <input type="text" name="name" v-model="form.name" />
                <span v-if="errors.name">{{ errors.name[0] }}</span>
            </div>
            <br>
            <div>
                <label for="">Email</label><br>
                <input type="text" name="email" v-model="form.email" />
                <span v-if="errors.email">{{ errors.email[0] }}</span>
            </div>
            <br>
            <div>
                <label for="">Contraseña</label><br>
                <input type="password" name="password" v-model="form.password" />
                <span v-if="errors.password">{{ errors.password[0] }}</span>
            </div>

            <br>

            <div>
                <label for="">Confirmar Contraseña</label><br>
                <input type="password" name="password" v-model="form.password_confirmation" />
                <span v-if="errors.password_confirmation">{{ errors.password_confirmation[0] }}</span>
            </div>

            <br>

            <div>
                <button style="padding: 1rem 2rem;" @click="register()" type="button">Registrarse</button>
            </div>

            <br>

            <!-- <router-link class="link" to="forgot-password"
            >Olvidaste tu Contraseña</router-link> -->
            <p v-if="message">
                {{ message }}
            </p>
        </form>
    </div>
</template>

<script>

export default {
    data() {
        return {
            message: null,
            form: {
                name: "",
                email: "",
                password: "",
                password_confirmation: "",
                
            },
            errors: {},
        };
    },

    mounted() {
        // if (this.$route.query.token)
        //     this.form.token = this.$route.query.token;
         if (this.$route.params.message)
            this.message = this.$route.params.message
    },


    methods: {
        async register() {
            try {
                const rs = await this.axios.post("/api/register", this.form);
                this.$router.push({
                    name: 'Login',
                    params: { message: rs.data.message, },
                });
                

            }
            catch (e) {

                this.errors = {},
                    this.message = null;

                if (e.response.data.errors)
                    this.errors = e.response.data.errors;

                if (e.response.data.message)
                    this.errors = e.response.data.message;
            }

        },
    },
};
</script>