<template>
	<div class="marg-div">
		{{ textoCL }}
	</div>
	<div class="marg-div">
		<button @click="show = !show">MENU</button>
	</div>
	<Transition name="fade">
		<MainMenu v-show="show" />
	</Transition>
	<div class="marg-div">
		<MainModal />
	</div>
</template>

<script>
import MainMenu from "./components/MainMenu.vue";
import MainModal from "./components/MainModal.vue";
export default {
	name: "App",
	components: { MainMenu, MainModal },
	data() {
		return {
			show: false,
			textoCL: "Hola Vue app...",
		};
	},
	beforeCreate() {
		console.log("Before Create =>", this.data, this.$el);
	},
	created() {
		console.log("Created =>", this.data, this.$el);
	},
	mounted() {
		console.log("Mounted =>", this.data, this.$el);
	},
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}

.marg-div {
	margin: 15px;
}

.fade-leave-to,
.fade-enter-from {
	opacity: 0;
}

.fade-leave-active,
.fade-enter-active {
	transition: opacity 0.5s ease;
}
</style>
