<script>
  import { page } from "$app/stores"; // Import page store
  import { derived } from "svelte/store";

  let menuOpen = false; // ✅ Fix menuOpen not defined error

  // Extract the current route (pathname)
  const currentPath = derived(page, ($page) => $page.url.pathname);
</script>

<nav class="fixed top-0 left-0 w-full bg-white dark:bg-gray-900 backdrop-blur-md shadow-lg z-50">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="flex justify-between items-center h-16">
      
      <!-- Logo -->
      <div class="text-2xl font-bold text-gray-800 dark:text-white tracking-wide">
        SvelteKit 🚀
      </div>

      <!-- Navigation Links (Desktop) ✅ FIXED -->
      <div class="hidden md:flex space-x-8">
        <a href="/" 
           class="relative px-3 py-2 font-medium transition duration-300
                  text-gray-700 dark:text-gray-300 hover:text-blue-600 dark:hover:text-blue-400 hover:underline"
           class:bg-gray-300={$currentPath === "/"}
           class:dark-bg-gray-700={$currentPath === "/"}>
          Home
        </a>
        <a href="/about" 
           class="relative px-3 py-2 font-medium transition duration-300
                  text-gray-700 dark:text-gray-300 hover:text-green-600 dark:hover:text-green-400 hover:underline"
           class:bg-gray-300={$currentPath === "/about"}
           class:dark-bg-gray-700={$currentPath === "/about"}>
          About
        </a>
        <a href="/contact" 
           class="relative px-3 py-2 font-medium transition duration-300
                  text-gray-700 dark:text-gray-300 hover:text-red-600 dark:hover:text-red-400 hover:underline"
           class:bg-gray-300={$currentPath === "/contact"}
           class:dark-bg-gray-700={$currentPath === "/contact"}>
          Contact
        </a>
        <a href="/carousel" 
           class="relative px-3 py-2 font-medium transition duration-300 
                  text-gray-700 dark:text-gray-300 
                  hover:text-purple-600 dark:hover:text-purple-400 
                  hover:underline"
           class:bg-gray-300={$currentPath === "/carousel"}  
           class:dark-bg-gray-700={$currentPath === "/carousel"}> 
          Carousel
        </a>
      </div>

      <!-- Dark Mode Toggle Inside Navbar -->
      <div class="hidden md:flex">
        <button 
          on:click={() => document.documentElement.classList.toggle('dark')}
          class="p-2 rounded-md bg-gray-200 dark:bg-gray-800 text-gray-700 dark:text-gray-300 shadow-md hover:bg-gray-300 dark:hover:bg-gray-700 transition">
          🌙
        </button>
      </div>

      <!-- Mobile Menu Button -->
      <button 
        class="md:hidden p-2 rounded-md text-gray-700 dark:text-gray-200 hover:bg-gray-300 dark:hover:bg-gray-700 transition"
        on:click={() => menuOpen = !menuOpen}>
        ☰
      </button>
    </div>
  </div>

  <!-- Mobile Dropdown Menu ✅ FIXED -->
  <div class="absolute w-full md:hidden transition-all duration-500 ease-in-out bg-white dark:bg-gray-800 shadow-md rounded-lg py-3 px-5"
       class:hidden={!menuOpen}>
    <a href="/" 
       class="block relative px-3 py-2 font-medium transition duration-300
              text-gray-700 dark:text-gray-300 hover:text-blue-600 dark:hover:text-blue-400 hover:underline"
       class:bg-gray-300={$currentPath === "/"}
       class:dark-bg-gray-700={$currentPath === "/"}>
      Home
    </a>
    <a href="/about" 
       class="block relative px-3 py-2 font-medium transition duration-300
              text-gray-700 dark:text-gray-300 hover:text-green-600 dark:hover:text-green-400 hover:underline"
       class:bg-gray-300={$currentPath === "/about"}
       class:dark-bg-gray-700={$currentPath === "/about"}>
      About
    </a>
    <a href="/contact" 
       class="block relative px-3 py-2 font-medium transition duration-300
              text-gray-700 dark:text-gray-300 hover:text-red-600 dark:hover:text-red-400 hover:underline"
       class:bg-gray-300={$currentPath === "/contact"}
       class:dark-bg-gray-700={$currentPath === "/contact"}>
      Contact
    </a>
    <a href="/carousel" 
       class="block relative px-3 py-2 font-medium transition duration-300 
              text-gray-700 dark:text-gray-300 
              hover:text-purple-600 dark:hover:text-purple-400 
              hover:underline"
       class:bg-gray-300={$currentPath === "/carousel"}  
       class:dark-bg-gray-700={$currentPath === "/carousel"}> 
      Carousel
    </a>
  </div>
</nav>
