<script>
  const experience = [
    {
      date: "February 2024 – Present",
      title: "Software Developer | Elvicto Technologies",
      description:
        "Developed and maintained production-level mobile applications using Flutter with Clean Architecture and Provider for state management. Worked on Node.js and Angular projects, and contributed to small AI/ML tasks such as object detection using YOLOv5.",
      linkText: "View Project",
      linkUrl: "#"
    },
    {
      date: "December 2023 – January 2024",
      title: "AI/ML Intern | ElsysLabs Technologies",
      description:
        "Built a resume analyzer API using FastAPI, leveraging Jaccard similarity for text matching. Containerized the application and deployed it using Docker.",
      linkText: "Learn More",
      linkUrl: "#"
    }
  ];
</script>

<h2 class="text-3xl font-bold text-white mb-8">Professional Experience</h2>

<ol class="relative border-s border-gray-200 dark:border-gray-700">
  {#each experience as item}
    <li class="mb-10 ms-4">
      <div class="absolute w-3 h-3 bg-gray-200 rounded-full mt-1.5 -start-1.5 border border-white dark:border-gray-900 dark:bg-gray-700"></div>
      <time class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">{item.date}</time>
      <h3 class="text-lg font-semibold bg-gradient-to-r from-white to-bg-violet-400">{item.title}</h3>
      <p class="mb-4 text-base font-normal text-gray-500 dark:text-gray-400">{item.description}</p>
      <!-- {#if item.linkUrl}
        <a
          href={item.linkUrl}
          class="inline-flex items-center px-4 py-2 text-sm font-medium text-gray-900 bg-white border border-gray-200 rounded-lg hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-4 focus:outline-none focus:ring-gray-100 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700 dark:focus:ring-gray-700"
        >
          {item.linkText}
          <svg class="w-3 h-3 ms-2 rtl:rotate-180" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 10">
            <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 5h12m0 0L9 1m4 4L9 9"/>
          </svg>
        </a>
      {/if} -->
    </li>
  {/each}
</ol>
