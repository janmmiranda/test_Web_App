<template>
	<v-toolbar fixed class="cyan">
		<v-toolbar-title class="mr-4">
			Web App
		</v-toolbar-title>
		
		<!-- Todo: Implement Me
		<v-toolbar-items>
			<v-btn flat dark>
				Browse
			</v-btn>
		</v-toolbar-items> -->

		<v-spacer></v-spacer>

		<v-toolbar-items>
			<v-btn 
			v-if="!$store.state.isUserLoggedIn"
			flat dark to="register">
				Sign Up
			</v-btn>
			<v-btn 
			v-if="!$store.state.isUserLoggedIn"
			flat dark to="login">
				Login
			</v-btn>
		</v-toolbar-items>
	</v-toolbar>
</template>

<script>
export default {

}
</script>

<style scoped>

</style>