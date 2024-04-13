<script>
  let hasAdm = false;
  let adms = [];

  let adm = {
    description: '',
    logic: '',
    significance: '',
    consequences: '',
  }

  const toggleDataShared = () => {
    hasAdm = !hasAdm;
  }

  const addAdm = () => {
    adms = [
      ...adms,
      adm
    ]

    adm = {};
  }

  const removeAdm = (localAdm) => {
    adms = adms.filter(adm => (
      adm.description !== localAdm.description &&
      adm.logic !== localAdm.logic &&
      adm.significance !== localAdm.significance &&
      adm.consequences !== localAdm.consequences
    ));

    adm = {};
  }

</script>

<div>
  <div>
    <label for="dataShared" class="block text-base font-medium leading-6 text-gray-900">
      Do you make any automated decisions as a result of processing personal data?
    </label>
    <!-- Enabled: "bg-sky-600", Not Enabled: "bg-gray-200" -->
    <button id="dataShared" on:click={toggleDataShared} type="button" class={`${hasAdm? 'bg-sky-600': 'bg-gray-200'} relative inline-flex h-6 w-11 flex-shrink-0 cursor-pointer rounded-full border-2 border-transparent transition-colors duration-200 ease-in-out focus:outline-none mt-4`} role="switch" aria-checked="false">
      <span class="sr-only">Use setting</span>
      <!-- Enabled: "translate-x-5", Not Enabled: "translate-x-0" -->
      <span aria-hidden="true" class={`${hasAdm? 'translate-x-5': 'translate-x-0'} pointer-events-none inline-block h-5 w-5 transform rounded-full bg-white shadow ring-0 transition duration-200 ease-in-out`}></span>
    </button>
  </div>

  {#if hasAdm}
    <div class="mt-2 p-8 rounded shadow-sm border">
      <div>
        <label for="description" class="block text-base font-medium leading-6 text-gray-900">
          Explain what the automated process is as per Article 22.
        </label>

        <div class="mt-1">
          <input
            bind:value={adm.description}
            type="text" name="description" id="description" class="px-2 block w-full rounded-md border-0 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-sky-600 sm:text-sm sm:leading-6"
          />
        </div>
      </div>

      <div class="mt-1">
        <label for="logic" class="block text-base font-medium leading-6 text-gray-900">
          Describe how the automated decision making works.
        </label>

        <div class="mt-1">
          <input
            bind:value={adm.logic}
            type="text" name="logic" id="logic" class="px-2 block w-full rounded-md border-0 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-sky-600 sm:text-sm sm:leading-6"
          />
        </div>
      </div>

      <div class="mt-1">
        <label for="significance" class="block text-base font-medium leading-6 text-gray-900">
          What is the significance of the automated decision making?
        </label>

        <div class="mt-1">
          <input
            bind:value={adm.significance}
            type="text" name="significance" id="significance" class="px-2 block w-full rounded-md border-0 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-sky-600 sm:text-sm sm:leading-6"
          />
        </div>
      </div>

      <div class="mt-1">
        <label for="consequences" class="block text-base font-medium leading-6 text-gray-900">
          What are the consequences of the automated decision?
        </label>

        <div class="mt-1">
          <input
            bind:value={adm.consequences}
            type="text" name="consequences" id="consequences" class="px-2 block w-full rounded-md border-0 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-sky-600 sm:text-sm sm:leading-6"
          />
        </div>
      </div>

      <div class="flex justify-start mt-8">
        <button on:click={addAdm} type="button" class="w-32 justify-center inline-flex items-center gap-x-1.5 rounded-md bg-sky-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-sky-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-sky-600">
          Add Transfer
        </button>

        <div class="flex flex-row ml-2 overflow-scroll space-x-2">
          {#each adms as localAdm}
            <span class="isolate inline-flex rounded-md shadow-sm">
              <button on:click={() => adm = localAdm} type="button" class="relative inline-flex items-center gap-x-1.5 rounded-l-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 ring-1 ring-inset ring-gray-300 hover:bg-gray-50 focus:z-10">
                {#if localAdm.description.length < 10}
                  {localAdm.description}
                {:else}
                  {localAdm.description.substring(0, 10) + '...'}
                {/if}
              </button>
              <button on:click={() => removeAdm(localAdm)} type="button" class="relative -ml-px inline-flex items-center rounded-r-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 ring-1 ring-inset ring-gray-300 hover:bg-gray-50 focus:z-10">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M6 18 18 6M6 6l12 12" />
                </svg>
              </button>
            </span>
          {/each}
        </div>
      </div>
    </div>
  {/if}
</div>