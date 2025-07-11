<script lang="ts">
	export let icon: string;
	export let label: string;
</script>

<div class="flex w-full flex-col items-center justify-center rounded-xl bg-gray-100 py-3">
	<img src={icon} alt={label} class="h-5 w-5 mb-1" />
	<span class="text-sm font-medium text-gray-700">{label}</span>
</div>
