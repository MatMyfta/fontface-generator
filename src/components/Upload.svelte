<script>
  import { createEventDispatcher } from "svelte";
  import { uploadedFilesStore } from "../stores";
  const dispatch = createEventDispatcher();
  let files = [];

  const handleFileChange = (event) => {
    files = Array.from(event.target.files);
    console.log("Files selected in Step1:", files);
  };

  const proceedToNext = () => {
    if (files.length > 0) {
      uploadedFilesStore.set(files);
      dispatch("nextStep");
      //   dispatch("filesUploaded", { files });
    }
  };
</script>

<div class="bg-white p-6 rounded shadow-md">
  <div class="text-xl font-bold mb-4">Upload Fonts</div>
  <input
    type="file"
    multiple
    accept=".ttf,.otf,.woff,.woff2"
    on:change={handleFileChange}
    class="block w-full mb-4"
  />
  <button
    on:click={proceedToNext}
    class="bg-blue-500 text-white px-4 py-2 rounded">Next</button
  >
</div>
