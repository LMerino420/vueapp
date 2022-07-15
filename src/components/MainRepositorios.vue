<template>
	<div>
		Composition <br />
		{{ texto }} <br />
		{{ contador }}
	</div>
</template>

<script>
import { reactive, ref } from "vue";

export default {
	setup() {
		const contador = reactive({ counter: 0 });
		const texto = ref("Esto es un texto con ref");

		setInterval(() => contador.counter++, 500);

		return {
			contador,
			texto,
		};
	},
};
</script>
