<script>
  import ArrowSeparator from "$lib/components/Stepper/ArrowSeparator.svelte";

  export let steps = [];
  export let onClick;

</script>

<nav aria-label="Progress">
  <ol role="list" class="divide-y divide-gray-300 rounded-md border border-gray-300 md:flex md:divide-y-0">
    {#each steps as step, index}
      <li class="relative md:flex md:flex-1">
        <!-- Completed Step -->
        {#if step.current}
          <button on:click={() => onClick(step, index)} class="cursor-pointer flex items-center px-6 py-4 text-sm font-medium" aria-current="step">
            <span class="flex h-10 w-10 flex-shrink-0 items-center justify-center rounded-full border-2 border-sky-600">
              <span class="text-sky-600">{step.number}</span>
            </span>
            <span class="ml-4 text-sm font-medium text-sky-600">{step.title}</span>
          </button>
        {:else if step.completed}
          <button on:click={() => onClick(step, index)} class="cursor-pointer group flex w-full items-center">
            <span class="flex items-center px-6 py-4 text-sm font-medium">
              <span class="flex h-10 w-10 flex-shrink-0 items-center justify-center rounded-full bg-sky-600 group-hover:bg-sky-800">
                <svg class="h-6 w-6 text-white" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
                  <path fill-rule="evenodd" d="M19.916 4.626a.75.75 0 01.208 1.04l-9 13.5a.75.75 0 01-1.154.114l-6-6a.75.75 0 011.06-1.06l5.353 5.353 8.493-12.739a.75.75 0 011.04-.208z" clip-rule="evenodd" />
                </svg>
              </span>
              <span class="ml-4 text-sm font-medium text-gray-900">{step.title}</span>
            </span>
          </button>
        {:else}
          <button disabled on:click={() => onClick(step, index)} class="cursor-pointer group flex items-center">
            <span class="flex items-center px-6 py-4 text-sm font-medium">
              <span class="flex h-10 w-10 flex-shrink-0 items-center justify-center rounded-full border-2 border-gray-300 group-hover:border-gray-400">
                <span class="text-gray-500 group-hover:text-gray-900">{step.number}</span>
              </span>
              <span class="ml-4 text-sm font-medium text-gray-500 group-hover:text-gray-900">{step.title}</span>
            </span>
          </button>
        {/if}

        {#if index < steps.length - 1}
          <ArrowSeparator />
        {/if}
      </li>
    {/each}
  </ol>
</nav>
