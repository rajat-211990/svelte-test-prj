<script lang="ts">
  let menuOpen = false;
</script>

<nav class="fixed top-0 left-0 w-full bg-white/30 dark:bg-gray-900/30 backdrop-blur-md shadow-lg z-50">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="flex justify-between items-center h-16">
      
      <!-- Logo -->
      <div class="text-2xl font-bold text-gray-800 dark:text-white tracking-wide">
        SvelteKit 🚀
      </div>

      <!-- Navigation Links (Desktop) -->
      <div class="hidden md:flex space-x-8">
        <a href="/" class="nav-link">Home</a>
        <a href="/about" class="nav-link">About</a>
        <a href="/contact" class="nav-link">Contact</a>
      </div>

      <!-- Mobile Menu Button -->
      <button 
        class="md:hidden p-2 rounded-md text-gray-700 dark:text-gray-200 hover:bg-gray-300 dark:hover:bg-gray-700 transition"
        on:click={() => menuOpen = !menuOpen}>
        ☰
      </button>
    </div>
  </div>

  <!-- Mobile Dropdown Menu -->
  <div class="absolute w-full md:hidden transition-all duration-500 ease-in-out"
       class:translate-y-0={menuOpen}
       class:-translate-y-full={!menuOpen}>
    <div class="bg-white dark:bg-gray-800 shadow-md rounded-lg py-3 px-5">
      <a href="/" class="block nav-link">Home</a>
      <a href="/about" class="block nav-link">About</a>
      <a href="/contact" class="block nav-link">Contact</a>
    </div>
  </div>
</nav>

<!-- TailwindCSS Styling -->
<style>
  @tailwind base;
  @tailwind components;
  @tailwind utilities;

  .nav-link {
    @apply text-gray-700 dark:text-gray-300 relative px-3 py-2 font-medium transition duration-300;
  }

  .nav-link::after {
    content: "";
    position: absolute;
    left: 50%;
    bottom: 0;
    width: 0%;
    height: 2px;
    background-color: #2563eb;
    transition: all 0.3s ease-in-out;
    transform: translateX(-50%);
  }

  .nav-link:hover::after {
    width: 100%;
  }
</style>
