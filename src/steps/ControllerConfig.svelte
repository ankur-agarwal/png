<script>
  let name = '';
  let representativeName = '';
  let representativeEmail = '';
  let dataProtectionOfficerEmail = '';
  let dataControllerEmail = '';

  let selectedYes = false;
  let selectedNo = false;

  let dataProtectionOfficerYes = false;
  let dataProtectionOfficerNo = false;

  const handleYes = () => {
    selectedNo = false;
    selectedYes = !selectedYes;
  }

  const handleNo = () => {
    selectedYes = false;
    selectedNo = !selectedNo;
  }

  const handleDataProtectionOfficerYes = () => {
    dataProtectionOfficerNo = false;
    dataProtectionOfficerYes = !dataProtectionOfficerYes;
  }

  const handleDataProtectionOfficerNo = () => {
    dataProtectionOfficerYes = false;
    dataProtectionOfficerNo = !dataProtectionOfficerNo;
  }

</script>

<div>
  <div>
    <label for="name" class="block text-base font-medium leading-6 text-gray-900">Data Controller's Name</label>
    <div class="mt-2">
      <input
        bind:value={name}
        type="text" name="name" id="name" class="block w-full rounded-md border-0 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-sky-600 sm:text-sm sm:leading-6"
      />
    </div>
  </div>

  <div class="mt-4">
    <label for="representative" class="block text-base font-medium leading-6 text-gray-900">
      Do you have a Representative as per Article 27 of the GDPR?
    </label>

    <span id="representative" class="isolate inline-flex rounded-md shadow-sm mt-2">
      <button on:click={handleYes} type="button" class={`relative inline-flex items-center rounded-l-md px-3 py-2 text-sm font-semibold ring-1 ring-inset ring-gray-300 hover:bg-green-50 focus:z-10 ${selectedYes? 'bg-green-700 text-white hover:bg-green-800': 'text-green-900 bg-white'}`}>Yes</button>
      <button on:click={handleNo} type="button" class={`relative -ml-px inline-flex items-center rounded-r-md px-3 py-2 text-sm font-semibold ring-1 ring-inset ring-gray-300 hover:bg-red-50 focus:z-10 ${selectedNo? 'bg-red-700 text-white hover:bg-red-800': 'text-red-900 bg-white'}`}>No</button>
    </span>
  </div>

  {#if selectedYes}
    <div class="mt-8">
      <label for="representativeName" class="block text-base font-medium leading-6 text-gray-900">
        Representative's Name
      </label>

      <div class="mt-2">
        <input
          bind:value={representativeName}
          type="text" name="representativeName" id="representativeName" class="block w-full rounded-md border-0 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-sky-600 sm:text-sm sm:leading-6"
        />
      </div>
    </div>

    <div class="mt-4">
      <label for="representativeEmail" class="block text-base font-medium leading-6 text-gray-900">
        Representative's Email Address
      </label>

      <div class="mt-2">
        <input
          bind:value={representativeEmail}
          type="email" name="representativeEmail" id="representativeEmail" class="block w-full rounded-md border-0 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-sky-600 sm:text-sm sm:leading-6"
        />
      </div>
    </div>
  {/if}

  {#if selectedNo}
    <div class="mt-4">
      <label for="dataProtectionOfficer" class="block text-base font-medium leading-6 text-gray-900">
        Do you have a Data Protection Officer?
      </label>

      <span id="dataProtectionOfficer" class="isolate inline-flex rounded-md shadow-sm mt-2">
        <button on:click={handleDataProtectionOfficerYes} type="button" class={`relative inline-flex items-center rounded-l-md bg-white px-3 py-2 text-sm font-semibold ring-1 ring-inset ring-gray-300 hover:bg-green-50 focus:z-10 ${dataProtectionOfficerYes? 'bg-green-700 text-white hover:bg-green-800': 'text-green-900'}`}>Yes</button>
        <button on:click={handleDataProtectionOfficerNo} type="button" class={`relative -ml-px inline-flex items-center rounded-r-md bg-white px-3 py-2 text-sm font-semibold ring-1 ring-inset ring-gray-300 hover:bg-red-50 focus:z-10 ${dataProtectionOfficerNo? 'bg-red-700 text-white hover:bg-red-800': 'text-red-900'}`}>No</button>
      </span>
    </div>

    {#if dataProtectionOfficerYes}
      <div class="mt-4">
        <label for="dataProtectionOfficerEmail" class="block text-base font-medium leading-6 text-gray-900">
          Data Protection Officer's Email Address
        </label>

        <div class="mt-2">
          <input
            bind:value={dataProtectionOfficerEmail}
            type="email" name="dataProtectionOfficerEmail" id="dataProtectionOfficerEmail" class="block w-full rounded-md border-0 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-sky-600 sm:text-sm sm:leading-6"
          />
        </div>
      </div>
    {/if}

    {#if (dataProtectionOfficerNo || dataProtectionOfficerYes)}
      <div class="mt-4">
        <label for="dataControllerEmail" class="block text-base font-medium leading-6 text-gray-900">
          Data Controller's Email Address
        </label>

        <div class="mt-2">
          <input
            bind:value={dataControllerEmail}
            type="email" name="dataControllerEmail" id="dataControllerEmail" class="block w-full rounded-md border-0 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-sky-600 sm:text-sm sm:leading-6"
          />
        </div>
      </div>
    {/if}
  {/if}
</div>