<script>
  export let steps = [];

  let scrollContainer;

  function scrollLeft() {
    scrollContainer.scrollBy({ left: -300, behavior: "smooth" });
  }

  function scrollRight() {
    scrollContainer.scrollBy({ left: 300, behavior: "smooth" });
  }
</script>

<div class="relative py-8">

  
  <button
    on:click={scrollLeft}
    class="hidden lg:flex absolute left-0 top-1/2 -translate-y-1/2 z-10 bg-violet-500 text-white p-3 rounded-full shadow-lg hover:bg-violet-600"
  >
    ←
  </button>

  <div
    bind:this={scrollContainer}
    class="flex gap-6 overflow-x-auto snap-x snap-mandatory px-2 scrollbar-hide"
  >
    {#each steps as step, i}
      <div
        class="card bg-base-100 w-80 shadow-xl snap-center shrink-0 rounded-2xl overflow-hidden relative"
      >
        <figure class="relative">
          <img
            src={Array.isArray(step.images)
              ? step.images[0]
              : step.images || "/assets/images/parkochi_screen_0.png"}
            alt={step.name}
            class="object-cover w-full h-44 rounded-t-2xl"
          />

          <!-- GitHub icon button on image -->
          {#if step.links?.github}
            <a
              href={step.links.github}
              target="_blank"
              class="absolute top-2 right-2 bg-gray-800/70 hover:bg-gray-900 text-white p-2 rounded-full transition"
              aria-label="GitHub link"
            >
              <i class="fa-brands fa-github text-lg"></i>
            </a>
          {/if}
        </figure>

        <div class="card-body">
          <h2 class="card-title text-white">{step.name}</h2>

          {#if step.tagline}
            <p class="text-gray-300">{step.tagline}</p>
          {/if}

          {#if step.tech}
            <p class="text-sm text-violet-400">{step.tech.join(" • ")}</p>
          {/if}

          <div class="flex flex-wrap gap-2 mt-3">
            <div class="flex flex-wrap gap-2 mt-3">
              {#if step.links?.playstore}
                <a
                  href={step.links.playstore}
                  target="_blank"
                  class="flex items-center gap-1 px-3 py-1 text-xs bg-green-500 hover:bg-green-600 text-white rounded-full whitespace-nowrap"
                >
                  <i class="fa-brands fa-google-play"></i>
                  <span>Play Store</span>
                </a>
              {/if}

              {#if step.links?.appStore}
                <a
                  href={step.links.appStore}
                  target="_blank"
                  class="flex items-center gap-1 px-3 py-1 text-xs bg-gray-800 hover:bg-gray-900 text-white rounded-full whitespace-nowrap"
                >
                  <i class="fa-brands fa-apple"></i>
                  <span>App Store</span>
                </a>
              {/if}

              {#if step.links?.web}
                <a
                  href={step.links.web}
                  target="_blank"
                  class="flex items-center gap-1 px-3 py-1 text-xs bg-blue-500 hover:bg-blue-600 text-white rounded-full whitespace-nowrap"
                >
                  <i class="fa-solid fa-globe"></i>
                  <span>Web</span>
                </a>
              {/if}
            </div>
          </div>
        </div>
      </div>
    {/each}
  </div>

  <button
    on:click={scrollRight}
    class="hidden lg:flex absolute right-0 top-1/2 -translate-y-1/2 z-10 bg-violet-500 text-white p-3 rounded-full shadow-lg hover:bg-violet-600"
  >
    →
  </button>
</div>

<style>
  .scrollbar-hide::-webkit-scrollbar {
    display: none;
  }
  .scrollbar-hide {
    scrollbar-width: none;
  }
</style>
