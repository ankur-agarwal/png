<script>
  import Stepper from "$lib/components/Stepper/index.svelte";
  import Footer from "$lib/components/Footer.svelte";
  import ControllerConfig from "../steps/ControllerConfig.svelte";
  import Recipients from "../steps/Recipients.svelte";

  let currentStep = 0;

  const steps = [{
    number: 1,
    title: 'Controller Config',
    id: 'controller-config',
    completed: false,
    current: true,
    component: ControllerConfig,
  }, {
    number: 2,
    title: 'Purpose for Processing',
    id: 'purpose-for-processing',
    completed: false,
    current: false,
    component: Recipients,
  }, {
    number: 3,
    title: 'Recipients of Data',
    id: 'recipients-of-data',
    completed: false,
    current: false,
    component: Recipients,
  }, {
    number: 4,
    title: 'Automated Decision Making',
    id: 'automated-decision-making',
    completed: false,
    current: false,
    component: Recipients,
  }, {
    number: 5,
    title: 'Transfers to 3rd Countries',
    id: 'transfers-to-3rd-countries',
    completed: false,
    current: false,
    component: Recipients,
  }];

  const handleNext = () => {
    // update current step
    steps[currentStep].current = false;

    // mark current step as completed
    steps[currentStep].completed = true;

    // move to next step
    currentStep += 1;
    steps[currentStep].current = true;
  };

</script>

<div class="flex justify-center h-screen">
  <div class="flex flex-col h-full p-4">
    <!-- Page Heading -->
    <div class="min-w-0 max-w-7xl mt-8">
      <h2 class="flex justify-center text-4xl font-semibold leading-7 text-gray-700 sm:truncate sm:text-4xl sm:tracking-tight">
        Build your Privacy Notice
      </h2>

      <div class="mt-8">
        <Stepper steps={steps} />
      </div>
    </div>

    <main class="flex-1 max-w-7xl mt-8 h-3/4 overflow-scroll">
      <div>
        <svelte:component this={steps[currentStep].component}/>
      </div>
    </main>

    <Footer onNext={handleNext} />
  </div>
</div>