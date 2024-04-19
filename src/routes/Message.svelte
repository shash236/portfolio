<script>
	import { afterUpdate } from "svelte";

	let completeText =
		"Hey there! I'm Shashwatik, a Software Engineer based in Bangalore. Passionate about crafting elegant solutions to complex problems, I thrive on following my curiosity wherever it leads. Presently, I specialize in backend development, with a focus on Spring Boot, at my current workplace.";
	let message = "";
	let messageOpacity = 0;
	let speed = 100;
	let i = 0;
	function typeWriter() {
		if (i < completeText.length) {
			message += completeText.charAt(i);
			// @ts-ignore
			document.getElementById("message").innerHTML +=
				completeText.charAt(i);
			i++;
			setTimeout(typeWriter, (speed += 10));
		}
	}

	afterUpdate(() => {
		setTimeout(() => {
			messageOpacity = 1;
		}, 3100);
		setTimeout(typeWriter, 3200);
	});
</script>

<p id="message" class="typed" style="opacity : {messageOpacity}">{message}</p>

<style>
	.typed {
		font-weight: 100;
		font-size: 1.75em;
		padding-top: 3em;
		text-align: center;
	}

	.typed:after {
		content: "|";
		animation: blink 1s infinite;
	}

	@keyframes blink {
		0% {
			opacity: 0;
		}
		100% {
			opacity: 1;
		}
	}

	@keyframes typing {
		from {
			width: 0;
		}
		to {
			width: 100%;
		}
	}
</style>
