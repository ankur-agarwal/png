<script>
  let dataShared = false;

  const toggleDataShared = () => {
    dataShared = !dataShared;
  }

  let recipientOptions = [
    'Affiliates',
    'Group Entities',
    'Public Authorities',
    'Law Enforcement',
    'Vendors',
    'Credit Reference Agencies',
    'Data Brokers',
    'Social Media Platforms',
    'Advertising and Marketing Partners',
    'Agents',
  ]

  let selectedRecipients = [];

  const handleRecipientClick = (recipient) => {
    if (selectedRecipients.includes(recipient)) {
      selectedRecipients = selectedRecipients.filter((item) => item !== recipient);
    } else {
      selectedRecipients = [...selectedRecipients, recipient];
    }
  }

</script>

<div>
  <div>
    <label for="dataShared" class="block text-base font-medium leading-6 text-gray-900">
      Is personal data shared or otherwise disclosed to any third parties (including vendors):
    </label>
    <!-- Enabled: "bg-sky-600", Not Enabled: "bg-gray-200" -->
    <button id="dataShared" on:click={toggleDataShared} type="button" class={`${dataShared? 'bg-sky-600': 'bg-gray-200'} relative inline-flex h-6 w-11 flex-shrink-0 cursor-pointer rounded-full border-2 border-transparent transition-colors duration-200 ease-in-out focus:outline-none mt-4`} role="switch" aria-checked="false">
      <span class="sr-only">Use setting</span>
      <!-- Enabled: "translate-x-5", Not Enabled: "translate-x-0" -->
      <span aria-hidden="true" class={`${dataShared? 'translate-x-5': 'translate-x-0'} pointer-events-none inline-block h-5 w-5 transform rounded-full bg-white shadow ring-0 transition duration-200 ease-in-out`}></span>
    </button>
  </div>

  {#if dataShared}
    <div class="mt-4">
      <div>
        <label for="dataShared" class="block text-base font-medium leading-6 text-gray-900">
          Categories of Recipients
        </label>

        <div class="mt-2">
          <div class="isolate flex flex-wrap rounded-md">
            {#each recipientOptions as recipient}
              <button
                on:click={() => handleRecipientClick(recipient)}
                type="button"
                class={`${selectedRecipients.includes(recipient) ? 'bg-sky-600 text-white hover:bg-sky-600' : 'bg-white text-gray-900 hover:bg-gray-50'} relative flex text-nowrap mr-2 mt-2 items-center rounded border border-sky-500 px-3 py-2 text-sm font-semibold focus:z-10`}
              >
                {recipient}
              </button>
            {/each}
          </div>
        </div>
      </div>
    </div>
  {/if}

</div>