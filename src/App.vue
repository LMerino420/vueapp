<template>
	<div class="marg-div">
		{{ textoCL }} <br />
		{{ mixinText }}
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
	<div class="marg-div">
		<MainRepositorios />
	</div>
</template>

<script>
import base from "@/mixins/base";
import MainMenu from "./components/MainMenu.vue";
import MainModal from "./components/MainModal.vue";
import MainRepositorios from "./components/MainRepositorios.vue";

export default {
	name: "App",
	mixins: [base],
	components: { MainMenu, MainModal, MainRepositorios },
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
