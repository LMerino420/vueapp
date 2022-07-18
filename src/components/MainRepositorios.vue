<template>
	<div>
		<h3>Composition [Variables Reactivas]</h3>
		[REF] ----> {{ texto }}<br />
		[REACTIVE/WATCHER] ----> {{ contador }} <br />
		[COMPUTED] ----> {{ fullName }} <br />
		[PROVEDE/INJECT] ----> {{ usrName }}
	</div>
</template>

<script>
import { reactive, ref, watch, computed, toRefs, inject } from "vue";

export default {
	props: {
		firstName: String,
		lastName: String,
	},
	setup(props, context) {
		console.log("CONTEXT =>", context);
		const contador = reactive({ counter: 0 });
		const texto = ref("Texto con ref");
		const { firstName, lastName } = toRefs(props);

		let inter = setInterval(() => contador.counter++, 400);

		watch(
			() => contador.counter,
			(actual, anterior) => {
				console.log("VAL INTER=>", actual);
				console.log("Val ANT=>", anterior);
				if (actual == 5) {
					console.log("llego a su limite");
					clearInterval(inter);
				}
			},
		);

		const fullName = computed(() => {
			return `${firstName.value} ${lastName.value}`;
		});

		const usrName = inject("userName");

		return {
			contador,
			texto,
			fullName,
			usrName,
		};
	},
};
</script>
