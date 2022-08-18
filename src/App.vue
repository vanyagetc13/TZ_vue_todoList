<template>
	<Aside />
	<Main />
</template>

<script>
import Aside from "@/components/Aside.vue"
import Main from "@/components/Main.vue"
export default {
	components: {
		Aside,
		Main
	},
	data(){
		return {
			dark_theme: false
		}
	},
	methods:{
		changeDarkThemeState(){
			this.dark_theme = !this.dark_theme
		}
	}
}
</script>

<style lang="scss">
*, *::after, *::before {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}
body {
	height: 100vh;
	background-color: #FAFAFA;
	font-size: 14px;
}
#app {
	font-family: Nunito, sans-serif;
	color: #282846;
	position: relative;
	width: 100vw;
	height: 100vh;
}
.pointer {
  cursor: pointer;
}
</style>
