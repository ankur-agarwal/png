<script>
  import Stepper from "$lib/components/Stepper/index.svelte";
  import Footer from "$lib/components/Footer.svelte";

  let currentStep = 1;

</script>

<div class="flex justify-center h-screen">
  <div class="flex flex-col h-full">
    <!-- Page Heading -->
    <div class="min-w-0 flex-1 max-w-7xl mt-8">
      <h2 class="flex justify-center text-4xl font-semibold leading-7 text-gray-700 sm:truncate sm:text-4xl sm:tracking-tight">
        Build your Privacy Notice
      </h2>

      <div class="mt-8">
        <Stepper />
      </div>
    </div>

    <main class="flex-1 max-w-7xl">
      <div></div>
    </main>

    <Footer />
  </div>
</div>