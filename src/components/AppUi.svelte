<script>
  import { onMount, onDestroy } from "svelte";
  import { fade, fly, scale } from "svelte/transition";

  let root;
  let card;
  let win;
  let prefersReduced = false;

  onMount(() => {
    win = globalThis?.window;

    prefersReduced = win.matchMedia("(prefers-reduced-motion: reduce)").matches;
    if (!prefersReduced) {
      win.addEventListener("pointermove", handlePointerMove);
    }
  });

  onDestroy(() => {
    if (!prefersReduced) {
      window.removeEventListener("pointermove", handlePointerMove);
    }
  });

  function handlePointerMove(e) {
    // small tilt / parallax effect for desktop-ish pointer devices
    if (!card) return;
    const rect = card.getBoundingClientRect();
    const cx = rect.left + rect.width / 2;
    const cy = rect.top + rect.height / 2;
    const dx = (e.clientX - cx) / rect.width; // -0.5 .. 0.5
    const dy = (e.clientY - cy) / rect.height;
    const rx = dy * 6; // rotateX degrees
    const ry = -dx * 12; // rotateY degrees
    const tz = 12 + Math.hypot(dx, dy) * 6; // perspective translateZ feel

    card.style.transform = `perspective(1000px) rotateX(${rx}deg) rotateY(${ry}deg) translateZ(${tz}px)`;
    // subtle background canvas shift
    root.style.setProperty("--bg-rot-x", `${rx * 0.15}deg`);
    root.style.setProperty("--bg-rot-y", `${ry * 0.08}deg`);
  }

  function resetTransform() {
    if (card) card.style.transform = "";
    if (root) {
      root.style.setProperty("--bg-rot-x", `0deg`);
      root.style.setProperty("--bg-rot-y", `0deg`);
    }
  }
</script>

<style>
  :global(.material-symbols-outlined) {
    font-variation-settings: 'FILL' 0, 'wght' 400, 'GRAD' 0, 'opsz' 24;
    line-height: 1;
  }

  /* small helpers for the glass card */
  .glass {
    /* frosted glass: semi transparent + backdrop blur */
    background: linear-gradient(180deg, rgba(255,255,255,0.72) 0%, rgba(255,255,255,0.60) 100%);
    -webkit-backdrop-filter: blur(12px) saturate(120%);
    backdrop-filter: blur(12px) saturate(120%);
    border: 1px solid rgba(255,255,255,0.4);
  }

  /* dark mode variant */
  :global(.dark) .glass {
    background: linear-gradient(180deg, rgba(20,20,22,0.45), rgba(20,20,22,0.28));
    border: 1px solid rgba(255,255,255,0.06);
    -webkit-backdrop-filter: blur(12px) saturate(160%);
    backdrop-filter: blur(12px) saturate(160%);
  }

  /* background canvas (sharp corners) */
  .canvas {
    position: absolute;
    left: 50%;
    top: 6%;
    transform-origin: center;
    width: 520px;
    height: 340px;
    translate: -50% 0;
    background: linear-gradient(135deg, rgba(47,103,255,0.06), rgba(47,103,255,0.02));
    box-shadow: 0 18px 40px rgba(16,24,40,0.12);
    border-radius: 6px; /* small radius for slightly softened sharp corners */
    transform: rotateX(var(--bg-rot-x, 0)) rotateY(var(--bg-rot-y, 0)) translateZ(-40px);
    transition: transform 220ms cubic-bezier(.2,.9,.2,1);
    pointer-events: none;
    z-index: 1;
  }

  @media (max-width: 640px) {
    .canvas { width: 420px; height: 280px; top: 4%; }
  }

  /* soft highlight line on canvas */
  .canvas::before {
    content: "";
    position: absolute;
    inset: 0;
    border-radius: 6px;
    background: linear-gradient(180deg, rgba(255,255,255,0.03), rgba(255,255,255,0.0));
    pointer-events: none;
  }

  /* card hover lift for touch/keyboard accessibility */
  .card-wrap:active .glass,
  .card-wrap:focus-within .glass {
    transform: translateY(-6px);
    transition: transform 160ms;
  }

  /* shadow-layers to make it feel 3D */
  .shadow-layer {
    position: absolute;
    inset: auto;
    left: 50%;
    transform: translateX(-50%);
    width: 72%;
    height: 42%;
    bottom: -28%;
    filter: blur(28px);
    background: rgba(15, 23, 42, 0.12);
    border-radius: 24px;
    z-index: 0;
    transition: transform 200ms, opacity 200ms;
  }

  /* when card tilts, nudge the shadow */
</style>

<!-- svelte-ignore a11y-no-static-element-interactions -->
<div bind:this={root} class="w-full min-h-screen flex items-start justify-center py-8 px-2 relative" on:mouseleave={resetTransform}>
  <!-- decorative canvas (sharp-ish corners) behind the card -->
  <div class="canvas"></div>

  <!-- Center column -->
  <div class="w-full max-w-[380px] relative z-10 transform scale-[0.8] origin-top">
    <!-- subtle top label -->
    <!-- <div class="text-slate-500 mb-3 pl-1 text-sm select-none">User Profile</div> -->

    <!-- shadow layer -->
    <div class="shadow-layer"></div>

    <!-- Card container (we use a wrapper to control transform) -->
    <div class="card-wrap relative mx-auto" style="transform-style: preserve-3d; perspective:1200px;">
      <!-- actual glass card -->
      <!-- svelte-ignore a11y-no-noninteractive-tabindex -->
      <div
        bind:this={card}
        class="glass rounded-[20px] p-4 pb-8 shadow-[0_10px_40px_rgba(2,6,23,0.08)] relative overflow-hidden"
        in:scale={{ duration: 320, start: 0.1 }}
        on:mouseleave={resetTransform}
        tabindex="0"
        role="region"
        aria-label="Profile card"
      >
        <!-- Header -->
        <div class="flex items-center justify-between px-4 py-3 bg-white/60 backdrop-blur-md rounded-2xl shadow-md">
  
  <!-- Back Button -->
  <button 
    aria-label="Back"
    class="p-2 rounded-xl hover:bg-white/40 active:scale-95 transition-all duration-200"
  >
    <i class="fa-solid fa-chevron-left text-slate-800 text-xl"></i>
  </button>

  <!-- Title -->
  <div class="text-slate-900 font-semibold text-lg">Profile</div>

  <!-- Settings Button -->
  <button 
    aria-label="Settings"
    class="p-2 rounded-xl hover:bg-white/40 active:scale-95 transition-all duration-200"
  >
    <i class="fa-solid fa-gear text-slate-800 text-xl animate-spin-slow"></i>
  </button>

</div>


        <!-- Profile avatar -->
        <div class="flex flex-col items-center mt-5">
          <div class="w-28 h-28 rounded-full ring-4 ring-white/95 shadow-md overflow-hidden"
               style="background-image: url('https://lh3.googleusercontent.com/aida-public/AB6AXuBr3AIJ12E2lr4iq2XPcz4qR6-8yPOUixJiHXFU0bD6fPr-UQWvpswtX9xKGDZucQKQR6QNPd_gqgbicYcC2F0vkV9K9JNDZXJKzaHqBj3OC98vczQQNeQ0qqSw77J-CrcloI7_IIMfYCrKrUONzQAVT8vvhECu8fpuenC-ijNuUwLIO_wmyyZbrl_hdA93bUdVugc6WdTrvWhYD7bVxevStd-ev5LHGHCifGlHW7pW7SuMV1q-R84wEjVuvQkyZGkzDZ6_i-Jd7Bk'); background-size:cover; background-position:center;"
               in:scale={{ duration: 420, start: 0.8 }}
          ></div>

          <div class="mt-4 text-slate-900 font-semibold text-[20px]" in:fade={{ duration: 320 }}>Alex Doe</div>

          <button class="mt-4 px-6 py-2.5 rounded-xl bg-gradient-to-r from-[#2F67FF] to-[#3A8DFF] text-white font-medium shadow-sm active:scale-95 transition transform-gpu"
                  in:fly={{ y: 12, duration: 360 }}>
            Edit Profile
          </button>
        </div>

        <!-- info card (frosted inner card) -->
        <div class="mt-6 px-1">
          <div class="bg-white/60 dark:bg-slate-900/28 rounded-xl p-3 border border-white/60 dark:border-white/6 glass">
            <!-- item -->
            <div class="flex items-center justify-between py-2">
              <div class="flex items-center gap-3">
                <div class="w-9 h-9 rounded-lg flex items-center justify-center bg-[#E8F0FF] text-[#2F67FF]">
                  <span class="fa-solid fa-envelope text-xl"></span>
                </div>
                <div class="text-slate-900 font-medium">Email</div>
              </div>
              <div class="text-slate-600 text-sm">alex.doe@email.com</div>
            </div>

            <div class="h-px bg-slate-200/60 my-2"></div>

            <div class="flex items-center justify-between py-2">
              <div class="flex items-center gap-3">
                <div class="w-9 h-9 rounded-lg flex items-center justify-center bg-[#E8F0FF] text-[#2F67FF]">
                  <span class="fa-solid fa-phone text-xl"></span>
                </div>
                <div class="text-slate-900 font-medium">Phone Number</div>
              </div>
              <div class="text-slate-600 text-sm">+1 123-456-7890</div>
            </div>

            <div class="h-px bg-slate-200/60 my-2"></div>

            <div class="flex items-center justify-between py-2">
              <div class="flex items-center gap-3">
                <div class="w-9 h-9 rounded-lg flex items-center justify-center bg-[#E8F0FF] text-[#2F67FF]">
                  <span class="fa-solid fa-envelope text-xl"></span>
                </div>
                <div class="text-slate-900 font-medium">Location</div>
              </div>
              <div class="text-slate-600 text-sm">San Francisco, CA</div>
            </div>
          </div>
        </div>

        <!-- about -->
        <div class="mt-6 px-1">
          <div class="text-slate-900 font-semibold mb-2">About</div>

          <div class="bg-white/60 dark:bg-slate-900/28 rounded-xl p-4 border border-white/60 dark:border-white/6 glass">
            <p class="text-slate-600 text-sm leading-relaxed">
              Product designer and travel enthusiast. Passionate about creating intuitive and beautiful user experiences. In my free time, you can find me exploring new trails or trying out new coffee shops.
            </p>
          </div>
        </div>
      </div> <!-- end glass card -->
    </div>
  </div>
</div>
