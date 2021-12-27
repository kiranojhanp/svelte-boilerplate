<script lang="ts">
	import { metatags } from "@roxi/routify";
	import Hello from "@components/Hello.svelte";

	metatags.title = "My Routify app";
	metatags.description = "Description coming soon...";
</script>

<h1 class="font-light text-6xl">Svelte boilerplate</h1>
<p>This is the first page of routify</p>

<Hello />
