<script>
  let dataSharedYes = false;
  let dataSharedNo = false;

  const handleYes = () => {
    dataSharedYes = !dataSharedYes;
    dataSharedNo = false;
  }

  const handleNo = () => {
    dataSharedYes = false;
    dataSharedNo = !dataSharedNo;
  }

</script>

<div>
  <div>
    <label for="dataShared" class="block text-base font-medium leading-6 text-gray-900">
      Do you make any automated decisions as a result of processing personal data?
    </label>
    <span id="dataShared" class="isolate inline-flex rounded-md shadow-sm mt-2">
      <button on:click={handleYes} type="button" class={`relative inline-flex items-center rounded-l-md px-3 py-2 text-sm font-semibold ring-1 ring-inset ring-gray-300 hover:bg-green-50 focus:z-10 ${dataSharedYes? 'bg-green-700 text-white hover:bg-green-800': 'text-green-900 bg-white'}`}>Yes</button>
      <button on:click={handleNo} type="button" class={`relative -ml-px inline-flex items-center rounded-r-md px-3 py-2 text-sm font-semibold ring-1 ring-inset ring-gray-300 hover:bg-red-50 focus:z-10 ${dataSharedNo? 'bg-red-700 text-white hover:bg-red-800': 'text-red-900 bg-white'}`}>No</button>
    </span>
  </div>
</div>