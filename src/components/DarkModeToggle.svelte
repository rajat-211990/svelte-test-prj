<script>
  import { onMount } from "svelte";

  let darkMode = false;

  // Check localStorage for previous mode
  onMount(() => {
    darkMode = localStorage.getItem("theme") === "dark";
    applyTheme();
  });

  function toggleDarkMode() {
    darkMode = !darkMode;
    localStorage.setItem("theme", darkMode ? "dark" : "light");
    applyTheme();
  }

  function applyTheme() {
    if (darkMode) {
      document.documentElement.classList.add("dark");  // Apply class to <html>
    } else {
      document.documentElement.classList.remove("dark");
    }
  }
</script>

<button
  on:click={toggleDarkMode}
  class="p-2 text-white bg-gray-800 dark:bg-gray-200 dark:text-gray-800 rounded-md shadow-md hover:bg-gray-700 dark:hover:bg-gray-300 transition duration-300"
>
  {darkMode ? "☀️ Light Mode" : "🌙 Dark Mode"}
</button>

