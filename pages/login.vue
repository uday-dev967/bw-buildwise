<template>
	<div class="login-page">
		<v-card elevation="6" class="login-form-card" light>
			<h1 class="text-center grey--text darken-3">Login</h1>
			<v-card-title class="grey--text darken-3">Welcome</v-card-title>
			<v-card-subtitle class="grey--text darken-1">sing-in to your account</v-card-subtitle>
			<v-card-text>
				<!-- <v-form @submit.prevent="login">
					<v-text-field
						v-model="email"
						:rules="emailValidationRules"
						label="Email or Username"
						outlined
						required
						type="email"
					></v-text-field>

					<v-text-field
						v-model="password"
						label="Password"
						outlined
						required
						:rules="passwordValidationRules"
						:append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
						:type="showPassword ? 'text' : 'password'"
						@click:append="showPassword = !showPassword"
					></v-text-field>
					<v-row justify="space-between" align="center">
						<v-col>
							<v-checkbox v-model="rememberMe" label="Remember Me"></v-checkbox>
						</v-col>
						<v-col>
							<v-btn text color="primary">Forgot Password?</v-btn>
						</v-col>
					</v-row>
					<v-btn type="submit" color="primary white--text" block> sign in </v-btn>
				</v-form> -->
				<form-builder :fields="loginFormFields" @form-submitted="login"></form-builder>
			</v-card-text>
		</v-card>
		<img src="../static/loginback.png" alt="loginback" class="login-page-image" />
	</div>
</template>

<script>
import FormBuilder from "~/components/FormBuilder.vue"
export default {
	name: "Login",
	components: {
		"form-builder": FormBuilder,
	},
	data() {
		return {
			email: "",
			password: "",
			showPassword: false,
			rememberMe: false,
			emailValidationRules: [
				(value) => !!value || "This field is required",
				(value) => value.indexOf("@") !== 0 || "Please Enter a valid Email eg:'abc@xyz.com'",
				(value) => value.includes("@") !== 0 || "Please Enter a valid Email eg:'abc@xyz.com'",
				(value) => value.indexOf(".") - value.indexOf("@") > 1 || "Please Enter a valid Email eg:'abc@xyz.com'",
			],
			passwordValidationRules: [(value) => !!value || "This field is required"],
		}
	},
	head() {
		return {
			title: "Login Page",
		}
	},
	methods: {
		login() {
			// Implement your login logic here
			// eslint-disable-next-line no-console
			console.log("Login with:", this.email, this.password)
		},
	},
}
</script>

<style lang="scss" scoped>
.login-page {
	height: 100vh;
	width: 100vw;
	background-color: #f7f7f9;
	display: flex;
	justify-content: center;
	align-items: center;
	position: relative;
	.login-form-card {
		position: absolute;
		width: 25rem;
		z-index: 1;
	}
	&-image {
		position: absolute;
		bottom: 0;
		left: 0;
		z-index: 0;
	}
}
</style>
