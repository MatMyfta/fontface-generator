<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let generatedCode;

  const copyToClipboard = () => {
    navigator.clipboard.writeText(generatedCode);
  };

  const goBack = () => {
    dispatch("goBack");
  };
</script>

<div class="bg-white p-6 rounded shadow-md">
  <h2 class="text-xl font-bold mb-4">Generated Code</h2>
  <pre class="bg-gray-100 p-4 rounded overflow-x-auto">
        <code>{generatedCode}</code>
    </pre>
  <div class="flex- justify-between mt-4">
    <button on:click={goBack} class="bg-gray-500 text-white px-4 py-2 rounded"
      >Back</button
    >
    <button
      on:click={copyToClipboard}
      class="bg-green-500 text-white px-4 py-2 rounded"
      >Copy to Clipboard</button
    >
  </div>
</div>
