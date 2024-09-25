<script>
    export let currentStep;
    const steps = ['Upload Fonts', 'Font Settings', 'Generated Code'];
</script>

<div class="w-full bg-white py-4 shadow-md">
    <div class="container mx-auto flex items-center justify-between">
        {#each steps as step, index}
            <div class="flex-1 text-center">
                <div class={`w-8 h-8 mx-auto rounded-full ${currentStep > index ? 'bg-green-500' : 'bg-gray-300'} text-white flex items-center justify-center`}>
                    {index + 1}
                </div>
                <div class="text-xs mt-2">{step}</div>
            </div>
            {#if index < steps.length - 1}
            <div class="w-1/6 border-t-2 mx-2" style="border-color: {currentStep > index + 1 ? 'green' : 'gray'}"></div>
            {/if}
        {/each}
    </div>
</div>