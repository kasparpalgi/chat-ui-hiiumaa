<script lang="ts">
  export let text: string;
  export let onClick: () => void = () => {};
</script>

<button
  class="w-full rounded-full cursor-pointer bg-[#F6F9FD] py-3 text-center font-medium text-gray-700 transition hover:bg-[#e5f0fc]"
  on:click={onClick}
>
  {text}
</button>
