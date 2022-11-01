<!-- <template>

    <div class="todo">
        <div class="container" id="container">
            <div class="form-container sign-up-container">
                <form action="#">
                    <h1>Create Account</h1>
                    <span>or use your email for registration</span>
                    <input type="text" placeholder="Name" />
                    <input type="email" placeholder="Email" />
                    <input type="password" placeholder="Password" />
                    <input type="confirm password" placeholder="confirm Password" />
                    <button>Sign Up</button>
                </form>
            </div>
            <div class="form-container sign-in-container">
                <form action="#">
                    <h1>Sign in</h1>
                    <span>or use your account</span>
                    <input type="email" placeholder="Email" />
                    <input type="password" placeholder="Password" />
                    <a href="#">Forgot your password?</a>
                    <button>Sign In</button>
                </form>
            </div>
            <div class="overlay-container">
                <div class="overlay">
                    <div class="overlay-panel overlay-left">
                        <h1>Welcome Back!</h1>
                        <p>
                            To keep connected with us please login with your
                            personal info
                        </p>
                        <button class="ghost" id="signIn">Sign In</button>
                    </div>
                    <div class="overlay-panel overlay-right">
                        <h1>Hello, Friend!</h1>
                        <p>
                            Enter your personal details and start journey with
                            us
                        </p>
                        <button class="ghost" id="signUp">Sign Up</button>
                    </div>
                </div>
            </div>
        </div>
    </div>

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

        const signUpButton = document.getElementById("signUp");
        const signInButton = document.getElementById("signIn");
        const container = document.getElementById("container");

        signUpButton.addEventListener("click", () => {
            container.classList.add("right-panel-active");
        });

        signInButton.addEventListener("click", () => {
            container.classList.remove("right-panel-active");
        });



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
</script> -->