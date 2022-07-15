<template>
	<div>
		<button @click="toggle">Modal</button>
		<teleport to="body">
			<div v-show="showM" class="modal">
				<h1>Titulo</h1>
				<p>Lorem ipsum dolor sit amet consectetur.</p>
				<button @click="toggle">Cerrar</button>
			</div>
		</teleport>
	</div>
</template>

<script>
export default {
	data() {
		return {
			showM: false,
		};
	},
	methods: {
		toggle() {
			this.showM = !this.showM;
		},
	},
};
</script>
