<template style="font-feature-settings; width: 100vw; text-align: center;">
    <h1>
        Recupera tu Contraseña
    </h1>
    <form>
        <input type="text" name="email" v-model="email" placeholder="Correo eletronico">
        <br>
        <br>
        <button @click="send_email" type="button" style="font-variant: small-caps; width: 10rem;">Confirmar</button>
        <span v-if="errors.email"> {{ errors.email[0] }} </span>

    </form>
</template>

<script>
export default {
    data() {
        return {
            message: null,
            email: "",
            errors: {},
        };
    },
    mounted() {
        if (this.$route.params.message)
            this.message = this.$route.params.message

    },

    methods: {
        async send_email() {
            try {
                const rs = await this.axios.post
                    ("/api/forgot-password",
                        { email: this.email }
                    );

                this.$router.push({
                    name: 'Login',
                    params: { message: rs.data.message, },
                });

            }
            catch (e) {
                console.log('nou')
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
  