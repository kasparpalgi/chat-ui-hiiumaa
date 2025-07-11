<script lang="ts">
	export let icon: string;
	export let text: string;
	export let hint: string = '';
</script>

<li class="flex items-center gap-3 text-sm font-medium text-gray-800">
	<img src={icon} alt={text} class="h-5 w-5" />
	<span>{text}</span>
	{#if hint}
		<span class="text-sm text-gray-400 ml-auto">{hint}</span>
	{/if}
</li>
