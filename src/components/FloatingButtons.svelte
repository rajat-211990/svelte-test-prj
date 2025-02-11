<script>
  import { onMount } from "svelte";
  import { goto } from "$app/navigation"; // For navigating to contact page

  // Scroll to top function
  function scrollToTop() {
    window.scrollTo({ top: 0, behavior: "smooth" });
  }

  // Scroll to bottom function
  function scrollToBottom() {
    window.scrollTo({ top: document.body.scrollHeight, behavior: "smooth" });
  }

  // Navigate to contact page
  function goToContact() {
    goto("/contact");
  }
</script>

<!-- Floating Button Container -->
<div class="fixed bottom-1/2 right-6 transform translate-y-1/2 flex flex-col space-y-4 z-50">
  
  <!-- Scroll to Top -->
  <button on:click={scrollToTop} 
          class="fab bg-blue-500 hover:bg-blue-700 text-white">
    ⬆
  </button>

  <!-- Scroll to Bottom -->
  <button on:click={scrollToBottom} 
          class="fab bg-green-500 hover:bg-green-700 text-white">
    ⬇
  </button>

  <!-- Contact Page -->
  <button on:click={goToContact} 
          class="fab bg-red-500 hover:bg-red-700 text-white">
    📞
  </button>

</div>

<style>
  .fab {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
    font-weight: bold;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease-in-out;
  }
</style>
