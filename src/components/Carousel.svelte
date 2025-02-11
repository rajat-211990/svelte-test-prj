<script>
  import { writable } from "svelte/store";

  // Use direct Unsplash image URLs instead of API-generated ones
  const images = [
    "https://images.unsplash.com/photo-1506748686214-e9df14d4d9d0?w=900&q=80",
    "https://images.unsplash.com/photo-1521747116042-5a810fda9664?w=900&q=80",
    "https://images.unsplash.com/photo-1519681393784-d120267933ba?w=900&q=80"
  ];

  let currentIndex = writable(0);

  function prevImage() {
    currentIndex.update((n) => (n === 0 ? images.length - 1 : n - 1));
  }

  function nextImage() {
    currentIndex.update((n) => (n === images.length - 1 ? 0 : n + 1));
  }
</script>

<div class="carousel-container">
  {#each images as img, i}
    <div class="carousel-slide" class:active={$currentIndex === i}>
      <img src={img} alt="Carousel Image" class="carousel-image" class:raised={$currentIndex === i} />
    </div>
  {/each}

  <!-- Left Button -->
  <button on:click={prevImage} class="carousel-btn left-btn">❮</button>

  <!-- Right Button -->
  <button on:click={nextImage} class="carousel-btn right-btn">❯</button>
</div>

<style>
  .carousel-container {
    position: relative;
    width: 900px;
    height: 500px;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: auto;
  }

  .carousel-slide {
    display: none;
    transition: transform 0.5s ease-in-out;
  }

  .carousel-slide.active {
    display: block;
  }

  .carousel-image {
    width: 100%;
    height: auto;
    object-fit: cover;
    transition: transform 0.4s ease-in-out;
  }

  .carousel-image.raised {
    transform: scale(1.1);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
  }

  .carousel-btn {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(255, 255, 255, 0.6);
    border: none;
    padding: 10px;
    font-size: 24px;
    cursor: pointer;
    transition: background 0.3s;
    border-radius: 50%;
  }

  .carousel-btn:hover {
    background: rgba(255, 255, 255, 0.9);
  }

  .left-btn {
    left: 10px;
  }

  .right-btn {
    right: 10px;
  }
</style>
