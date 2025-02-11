<script>
  import { onMount } from "svelte";
  import { loremText } from "$lib/stores/loremStore";  // ✅ Corrected import path

  onMount(async () => {
    let value;
    loremText.subscribe((v) => (value = v));
    if (!value) {
      const response = await fetch("/lorem.txt");
      const text = await response.text();
      loremText.set(text);
    }
  });
</script>

<div class="text-center p-10">
  <h1 class="text-4xl text-blue-600 font-extrabold">Welcome to SvelteKit! 🚀</h1>
  <p class="text-gray-700 text-lg mt-2">If you see this, your app is working correctly.</p>

  <h1 class="text-3xl text-blue-500 font-bold mt-6">Explore Our Features</h1>
  <p class="text-gray-700 text-lg">This is the home page with added content for scrolling.</p>

  <!-- Navigate to Services Page -->
  <a href="/services">
    <button class="mt-6 px-6 py-3 bg-blue-500 text-white rounded-md shadow-md hover:bg-blue-700 transition duration-300">
      Go to Services
    </button>
  </a>
</div>

<!-- Long Scrollable Text -->
<div class="p-6 max-w-3xl mx-auto text-lg leading-relaxed mt-10">
  {#if $loremText}
    <pre class="whitespace-pre-wrap text-gray-800 dark:text-gray-200">{$loremText}</pre>
  {:else}
    <p>Loading content...</p>
  {/if}
</div>
