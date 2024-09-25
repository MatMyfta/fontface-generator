<script>
  import ProgressBar from "./components/ProgressBar.svelte";
  import Upload from "./components/Upload.svelte";
  import FontSettings from "./components/FontSettings.svelte";
  import GeneratedCode from "./components/GeneratedCode.svelte";

  let currentStep = 1;
  // let uploadedFiles = [];
  let fontSettings = [];
  let generatedCode = "";

  const nextStep = () => (currentStep += 1);
  const prevStep = () => (currentStep -= 1);

  // const handleFilesUpload = (files) => {
  //   uploadedFiles = files;
  //   nextStep();
  // };

  const handleSettingsSubmit = (settings) => {
    fontSettings = settings;
    generateFontFaceCode();
    nextStep();
  };

  const generateFontFaceCode = () => {
    generatedCode = fontSettings
      .map(
        (setting) => `
      @font-face {
        font-family: '${setting.fontFamily}';
        src: url('${setting.fileName}');
        font-weight: ${setting.fontWeight};
        font-style: ${setting.fontStyle};
      }
    `
      )
      .join(`
`);
  };
</script>

<main class="bg-gray-100">
  <div class="min-h-screen bg-gray-100 flex flex-col">
    <ProgressBar {currentStep} />
    <div class="flex-grow container mx-auto p-4">
      {#if currentStep === 1}
        <!-- <Upload on:filesUploaded="{(e) => handleFilesUpload(e.detail.files)}" /> -->
        <Upload on:nextStep="{nextStep}" />
      {:else if currentStep === 2}
        <FontSettings
          on:settingsSubmitted="{(e) => handleSettingsSubmit(e.detail)}"
          on:goBack="{prevStep}"
        />
      {:else if currentStep === 3}
        <GeneratedCode {generatedCode} on:goBack="{prevStep}" />
      {/if}
    </div>
  </div>
</main>
