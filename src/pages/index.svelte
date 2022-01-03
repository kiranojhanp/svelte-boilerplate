<script lang="ts">
	import { metatags } from "@roxi/routify";
	import { fade, fly } from "svelte/transition";
	import { elasticOut } from "svelte/easing";

	metatags.title = "Home page";
	metatags.description = "This is my homepage";

	let visible = true;

	function spin(node: Element, { duration }) {
		return {
			duration,
			css: (t: number) => {
				const eased = elasticOut(t);
				return `
					transform: scale(${eased}) rotate(${eased * 1080}deg);
					color: hsl(
						${Math.trunc(t * 360)},
						${Math.min(100, 1000 - 1000 * t)}%,
						${Math.min(50, 500 - 500 * t)}%
					);`;
			},
		};
	}
</script>

<label>
	<input type="checkbox" bind:checked={visible} />
	visible
</label>

{#if visible}
	<div class="centered" out:fade in:fly={{ y: -200 }}>
		<span>transitions!</span>
	</div>
{/if}

<style>
	.centered {
		position: absolute;
		left: 50%;
		top: 50%;
		transform: translate(-50%, -50%);
	}

	span {
		position: absolute;
		transform: translate(-50%, -50%);
		font-size: 4em;
	}
</style>
