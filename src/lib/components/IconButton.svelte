<script lang="ts">
  export let icon: string;
  export let alt: string = '';
  export let active: boolean = false;
  export let onClick = () => {};
</script>

<button
  class={`p-1 rounded-md cursor-pointer transition ${active ? 'bg-blue-200' : 'hover:bg-gray-100'}`}
  on:click={onClick}
>
  <img src={icon} alt={alt} class="w-5 h-5" />
</button>
