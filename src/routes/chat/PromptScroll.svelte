<script>
  import PromptItem from '$lib/components/PromptItem.svelte';
  import { onMount } from 'svelte';

  /**
	 * @type {HTMLDivElement}
	 */
  let scrollContainer;

  const prompts = [
    { title: 'Cocktail creation', subtitle: 'with unique ingredients' },
    { title: 'Wearable tech', subtitle: 'and health tracking' },
    { title: 'Real estate', subtitle: 'investment tips' },
    { title: 'AI in fashion', subtitle: 'design & styling' },
    { title: 'Healthy meals', subtitle: 'quick & easy recipes' },
    { title: 'Crypto insights', subtitle: 'market trends' },
    { title: 'Fitness tips', subtitle: 'stay active daily' },
  ];

  // @ts-ignore
  function handleWheel(event) {
    if (event.deltaY !== 0) {
      event.preventDefault();
      // @ts-ignore
      scrollContainer.scrollLeft += event.deltaY;
    }
  }
</script>

<div
  bind:this={scrollContainer}
  class="w-full overflow-x-auto whitespace-nowrap py-2 px-1 scroll-smooth no-scrollbar"
  on:wheel|passive={handleWheel}
>
  <div class="flex">
    {#each prompts as prompt}
      <PromptItem title={prompt.title} subtitle={prompt.subtitle} />
    {/each}
  </div>
</div>

<style>
  .no-scrollbar::-webkit-scrollbar {
    display: none;
  }
  .no-scrollbar {
    -ms-overflow-style: none;
    scrollbar-width: none;
  }
</style>
