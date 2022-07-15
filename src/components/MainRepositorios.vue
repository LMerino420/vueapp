<template>
	<div>
		<h3>Composition [Variables Reactivas]</h3>
		[REF] ----> {{ texto }}<br />
		[REACTIVE | WATCHER] ----> {{ contador }} <br />
		[COMPUTED] ----> {{ fullName }}
	</div>
</template>

<script>
import { reactive, ref, watch, computed } from "vue";

export default {
	setup() {
		const contador = reactive({ counter: 0 });
		const texto = ref("Texto con ref");
		const firstName = ref("Lev");
		const lastName = ref("Merino");

		let inter = setInterval(() => contador.counter++, 400);

		watch(
			() => contador.counter,
			(actual, anterior) => {
				console.log("VAL INTER=>", actual);
				console.log("Val ANT=>", anterior);
				if (actual == 15) {
					console.log("llego a su limite");
					clearInterval(inter);
				}
			},
		);

		const fullName = computed(() => {
			return `${firstName.value} ${lastName.value}`;
		});

		return {
			contador,
			texto,
			fullName,
		};
	},
};
</script>
