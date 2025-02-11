<script>
  import { fade } from 'svelte/transition';
  import { page } from '$app/stores'; 
  import "../app.css";
  import DarkModeToggle from "../components/DarkModeToggle.svelte";
  import Navbar from "../components/Navbar.svelte";

</script>
<Navbar />

<!-- Add padding to push content below the navbar -->
<div class="pt-20">
  <slot />
</div>