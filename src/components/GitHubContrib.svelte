


<script>
  export let username = "bebialen"; // change to your GitHub username
</script>

<section id="github" class="py-16 text-center">
  <h2 class="text-3xl sm:text-4xl font-bold text-white mb-8">
    GitHub Contributions
  </h2>

  <!-- Contribution heatmap -->
  <img
    class="mx-auto rounded-lg shadow-lg"
    src={`https://ghchart.rshah.org/915DD2/${username}`}
    alt="GitHub Contributions Chart"
    loading="lazy"
  />

  <!-- Profile + Stats card -->
  <!-- <div class="mt-10 flex flex-col items-center gap-6">
    <a
      href={`https://github.com/${username}`}
      target="_blank"
      class="bg-white text-slate-900 px-6 py-3 rounded-full font-semibold hover:bg-violet-200 duration-200"
    >
      View My GitHub Profile →
    </a>

    <img
      src={`https://github-readme-stats.vercel.app/api?username=${username}&show_icons=true&theme=tokyonight`}
      alt="GitHub Stats"
      loading="lazy"
      class="rounded-lg"
    />
  </div> -->
</section>