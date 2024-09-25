<script>
  import { createEventDispatcher } from "svelte";
  import { uploadedFilesStore } from "../stores";
  const dispatch = createEventDispatcher();
  export let uploadedFiles = [];

  uploadedFilesStore.subscribe((files) => {
    uploadedFiles = files;
  });

  let settingsInitialized = false;
  let settings = [];

  $: if (!settingsInitialized && uploadedFiles.length > 0) {
    settings = uploadedFiles.length
      ? uploadedFiles.map((file) => ({
          fileName: file.name,
          fontFamily: file.name.split(".")[0],
          fontWeight: "400",
          fontStyle: "normal",
        }))
      : [];
    settingsInitialized = true;
  }
  $: console.log(settings);

  const fontWeights = [
    "100",
    "200",
    "300",
    "400",
    "500",
    "600",
    "700",
    "800",
    "900",
  ];
  const fontStyles = ["normal", "italic", "oblique"];

  const submitSettings = () => {
    dispatch("settingsSubmitted", settings);
  };

  const goBack = () => {
    dispatch("goBack");
  };
</script>

<div class="bg-white p-6 rounded shadow-md">
  <h2 class="text-xl font-bold mb-4">Font Settings</h2>
  {#each settings as setting, index}
    <div class="mb-4">
      <h3 class="font-semibold">{setting.fileName}</h3>
      <input
        type="text"
        bind:value={setting.fontFamily}
        placeholder="Font Family"
        class="block w-full mt-2 mb-2"
      />

      <label class="block mb-2" for="select-font-weight">Font Weight</label>
      <select
        bind:value={setting.fontWeight}
        id="select-font-weight"
        class="block w-full mb-2"
      >
        {#each fontWeights as weight}
          <option value={weight}>{weight}</option>
        {/each}
      </select>

      <label class="block mb-1" for="select-font-style">Font Style</label>
      <select
        bind:value={setting.fontStyle}
        id="select-font-style"
        class="block w-full mb-2"
      >
        {#each fontStyles as style}
          <option value={style}>{style}</option>
        {/each}
      </select>
    </div>
    <hr class="my-4" />
  {/each}
  <div class="flex justify-between">
    <button on:click={goBack} class="bg-gray-500 text-white px-4 py-2 rounded"
      >Back</button
    >
    <button
      on:click={submitSettings}
      class="bg-blue-500 text-white px-4 py-2 rounded">Generate</button
    >
  </div>
</div>
