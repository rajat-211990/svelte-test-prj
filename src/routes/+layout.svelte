<script>
  import "../app.css";
  import DarkModeToggle from "../components/DarkModeToggle.svelte";
</script>

<div class="flex justify-between items-center p-4 bg-gray-100 dark:bg-gray-800 shadow-md">
  <h1 class="text-xl font-bold text-gray-800 dark:text-white">My Svelte App</h1>
  <DarkModeToggle />
</div>

<slot />
