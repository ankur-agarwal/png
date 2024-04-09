<script>
  let transfers = [];
  let isDataShared = false;

  let transfer = {};

  const basis = [
    'Adequacy Decision',
    'Binding Corporate Rules',
    'Standard Contractual Clauses',
    'Approved Code of Conduct',
    'Approved Certification Mechanism',
    'Derogations'
  ]

  const handleBasisClick = (value) => {
    transfer.selectedBasis = value;
  }

  const toggleDataShared = () => {
    isDataShared = !isDataShared;
  }

  const addTransfer = () => {
    transfers = [
      ...transfers,
      transfer
    ]

    transfer = {};
  }

  const removeTransfer = (tr) => {
    transfers = transfers.filter((item) => (item.country !== tr.country && item.selectedBasis !== tr.selectedBasis));
    transfer = {};
  }
</script>

<div>
  <div>
    <label for="dataShared" class="block text-base font-medium leading-6 text-gray-900">
      Will any personal data be transferred outside of the EU/EEA?
    </label>
    <!-- Enabled: "bg-sky-600", Not Enabled: "bg-gray-200" -->
    <button id="dataShared" on:click={toggleDataShared} type="button" class={`${isDataShared? 'bg-sky-600': 'bg-gray-200'} relative inline-flex h-6 w-11 flex-shrink-0 cursor-pointer rounded-full border-2 border-transparent transition-colors duration-200 ease-in-out focus:outline-none mt-4`} role="switch" aria-checked="false">
      <span class="sr-only">Use setting</span>
      <!-- Enabled: "translate-x-5", Not Enabled: "translate-x-0" -->
      <span aria-hidden="true" class={`${isDataShared? 'translate-x-5': 'translate-x-0'} pointer-events-none inline-block h-5 w-5 transform rounded-full bg-white shadow ring-0 transition duration-200 ease-in-out`}></span>
    </button>
  </div>

  {#if isDataShared}
    <div class="mt-4 p-8 rounded shadow-sm border">
      <div>
        <label for="country" class="block text-base font-medium leading-6 text-gray-900">
          Which country outside of the EU/EEA will the data be transferred to?
        </label>

        <div class="mt-2">
          <input
            bind:value={transfer.country}
            type="text" name="country" id="country" class="px-2 block w-full rounded-md border-0 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-sky-600 sm:text-sm sm:leading-6"
          />
        </div>
      </div>

      <div class="mt-8">
        <label for="country" class="block text-base font-medium leading-6 text-gray-900">
          Select which basis the transfers will be based on from Adequacy Decision, SCCs, BCRs, CoCs, Derogation.
        </label>

        <div class="mt-4">
          <span class="isolate inline-flex rounded-md shadow-sm space-x-2">
            {#each basis as item}
              <button
                on:click={() => handleBasisClick(item)}
                type="button"
                class={`${transfer.selectedBasis === item ? 'bg-sky-600 text-white hover:bg-sky-600' : 'bg-white text-gray-900 hover:bg-gray-50'} relative inline-flex items-center rounded border border-sky-500 px-3 py-2 text-sm font-semibold focus:z-10`}
              >
                {item}
              </button>
            {/each}
          </span>
        </div>
      </div>

      <div class="flex justify-start mt-8">
        <button on:click={addTransfer} type="button" class="w-32 justify-center inline-flex items-center gap-x-1.5 rounded-md bg-sky-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-sky-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-sky-600">
          Add Transfer
        </button>

        <div class="flex flex-row ml-2 overflow-scroll space-x-2">
          {#each transfers as localTransfer}
            <span class="isolate inline-flex rounded-md shadow-sm">
              <button on:click={() => transfer = localTransfer} type="button" class="relative inline-flex items-center gap-x-1.5 rounded-l-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 ring-1 ring-inset ring-gray-300 hover:bg-gray-50 focus:z-10">
                {localTransfer.country}
              </button>
              <button on:click={() => removeTransfer(localTransfer)} type="button" class="relative -ml-px inline-flex items-center rounded-r-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 ring-1 ring-inset ring-gray-300 hover:bg-gray-50 focus:z-10">
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