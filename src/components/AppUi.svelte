<script>
  import { onMount, onDestroy } from "svelte";

  let root;
  let card;
  let layer1;
  let layer2;
  let layer3;
  let avatar;
  let shadow;

  let prefersReduced = false;

  onMount(() => {
    if (typeof window === "undefined") return;

    prefersReduced = window.matchMedia("(prefers-reduced-motion: reduce)").matches;

    if (!prefersReduced) {
      window.addEventListener("pointermove", handlePointerMove);
    }
  });

  onDestroy(() => {
    if (!prefersReduced) {
      window.removeEventListener("pointermove", handlePointerMove);
    }
  });

  function handlePointerMove(e) {
    if (!card) return;

    const rect = card.getBoundingClientRect();
    const cx = rect.left + rect.width / 2;
    const cy = rect.top + rect.height / 2;
    const dx = (e.clientX - cx) / rect.width;
    const dy = (e.clientY - cy) / rect.height;

    const rx = dy * 10;
    const ry = -dx * 14;
    const tz = Math.hypot(dx, dy) * 22;

    card.style.transform = `perspective(1200px) rotateX(${rx}deg) rotateY(${ry}deg) translateZ(${tz}px)`;

    layer1.style.transform = `translateX(${dx * 20}px) translateY(${dy * 20}px)`;
    layer2.style.transform = `translateX(${dx * 35}px) translateY(${dy * 35}px)`;
    layer3.style.transform = `translateX(${dx * 50}px) translateY(${dy * 50}px)`;

    avatar.style.transform = `translateZ(${40 + tz}px) scale(1.03)`;

    shadow.style.transform =
      `translateX(${dx * 18}px) translateY(${20 + dy * 12}px) scale(${1 + Math.abs(dx)})`;

    root?.style?.setProperty("--bg-rot-x", `${rx * 0.2}deg`);
    root?.style?.setProperty("--bg-rot-y", `${ry * 0.1}deg`);
  }
</script>

<div class="flex justify-center items-center min-h-screen" bind:this={root}>
  <div
    class="relative w-[320px] h-[620px] bg-white rounded-[40px] shadow-2xl overflow-hidden border border-black/10 transition-transform duration-300"
    bind:this={card}
  >

    <!-- Parallax Layers -->
    <div class="parallax-layer" bind:this={layer1}></div>
    <div class="parallax-layer" bind:this={layer2}></div>
    <div class="parallax-layer" bind:this={layer3}></div>

    <!-- Shadow under phone -->
    <div class="deep-shadow" bind:this={shadow}></div>

    <!-- Header -->
    <div class="flex items-center justify-between px-5 py-4 backdrop-blur-md bg-white/70">
      <button class="p-2 rounded-md hover:bg-black/10 active:scale-95 transition">
        <i class="fa-solid fa-arrow-left text-lg text-gray-700"></i>
      </button>

      <div class="text-slate-900 font-semibold text-lg">Profile</div>

      <button class="p-2 rounded-md hover:bg-black/10 active:scale-95 transition">
        <i class="fa-solid fa-gear text-lg text-gray-700"></i>
      </button>
    </div>

    <!-- Profile Area -->
    <div class="flex flex-col items-center mt-6">
      <div
        class="w-28 h-28 rounded-full ring-4 ring-white shadow-md overflow-hidden avatar-float"
        bind:this={avatar}
        style="background-image: url('assets/images/profile_2.png'); background-size: cover; background-position: center -20px;;"
      ></div>

      <h2 class="mt-4 text-xl font-semibold text-slate-900">Alan Bebido E.V</h2>
      <p class="text-gray-600 text-sm">Mobile App Developer</p>
    </div>

    <!-- Info Section -->
    <div class="mt-8 px-6 flex flex-col gap-5">
      <div class="flex items-center gap-3">
        <i class="fa-solid fa-location-dot text-gray-800"></i>
        <span class="text-gray-700 text-sm">India</span>
      </div>

      <div class="flex items-center gap-3">
        <i class="fa-solid fa-phone text-gray-800"></i>
        <span class="text-gray-700 text-sm">+91 7092755406</span>
      </div>

      <div class="flex items-center gap-3">
        <i class="fa-solid fa-envelope text-gray-800"></i>
        <span class="text-gray-700 text-sm">alanbebido2000@gmail.com</span>
      </div>
    </div>
  </div>
</div>

<style>
  .parallax-layer {
    position: absolute;
    inset: 0;
    pointer-events: none;
    transition: transform 0.25s cubic-bezier(.2, .9, .2, 1);
    will-change: transform;
  }

  .avatar-float {
    transition: transform 0.25s cubic-bezier(.2, .9, .2, 1);
    will-change: transform;
  }

  .deep-shadow {
    position: absolute;
    left: 50%;
    bottom: -40px;
    transform: translateX(-50%);
    width: 80%;
    height: 50px;
    background: rgba(0,0,0,0.2);
    filter: blur(28px);
    border-radius: 28px;
    transition: transform 0.25s cubic-bezier(.2, .9, .2, 1);
    will-change: transform;
  }
</style>
