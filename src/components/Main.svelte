<script>
  import { onMount } from "svelte";
  import Step from "./Step.svelte";
  import ProjectsCarousal from "./ProjectsCarousal.svelte";
  import * as Alert from "$lib/components/ui/alert";
  import { Motion } from "svelte-motion";
  import GitHubContrib from "./GitHubContrib.svelte";
  import Projects from "./ProjectsCarousal.svelte";
  import ProfessionalExperience from "./ProfessionalExperience.svelte";

//   import pkg from "@rive-app/canvas";

// let canvas;
// let riveInstance;

// onMount(async () => {
//   console.log("mounted");
  
//   try {
//     // Dynamic import inside onMount
//     const riveModule = await import("@rive-app/canvas");
//     console.log("Rive module:", riveModule);
    
//     // Try to access Rive from the module
//     const Rive = riveModule.default || riveModule.Rive;
    
//     if (!Rive) {
//       console.error("Could not find Rive constructor in module:", riveModule);
//       return;
//     }
    
//     riveInstance = new Rive({
//       src: "/assets/animations/tabbar_anime1.riv",
//       canvas: canvas,
//       autoplay: true,
//       stateMachines: ["State Machine 1"],
//       onLoad: () => {
//         console.log("✅ Rive loaded successfully");
//       },
//       onLoadError: (err) => {
//         console.error("❌ Rive load error:", err);
//       }
//     });
//   } catch (error) {
//     console.error("❌ Error loading Rive:", error);
//   }
  
//   return () => {
//     if (riveInstance) {
//       riveInstance.cleanup();
//     }
//   };
// });
  //TODO:Create a priority queuse for latest projects

  let steps = [
    {
      name: "Parkochi",
      tagline: "A smart way to discover and book parking instantly",
      icon: "fa-solid fa-square-parking",
      description:
        "Born from the frustration of hunting for parking. Parkochi helps drivers find safe parking spots in a few taps. I built the app with focus on smooth UX and near real-time updates.",
      role: "Flutter Developer",
      //TODO:Implement a screen carousal
      images: [
        "/assets/images/parkochi_screen_1.png",
        "/assets/images/parkochi_screen_2.jpg",
        "/assets/images/parkochi_screen_3.jpg",
        "/assets/images/parkochi_screen_4.jpg",
      ],
      tech: ["Flutter", "BLoc Architecture", "BLoC"],
      year: "2025",
      links: {
        github: "",
        playstore:
          "https://play.google.com/store/apps/details?id=com.csml.parkochi",
        appStore: "https://apps.apple.com/in/app/parkochi/id6742733665",
        web: "",
        demo: "",
      },
    },

    {
      name: "Block Breaker Game",
      tagline: "Classic Block Breaker Game- Deployed in vercel",
      icon: "fa-solid fa-gamepad",
      description: "A 2D puzzle game built using Flutter & Flame engine",
      role: "Flutter Game Developer",
      imageUrl: "",
      tech: ["Flutter", "Flame Engine", "vercel", "Collision detection"],
      year: "2025",
      links: {
        github: "https://github.com/bebialen/block_breaker",
        playstore: "",
        web: "https://block-breaker-six.vercel.app/",
        demo: "",
      },
    },
    {
      name: "Eduplay",
      tagline:
        "voice based AI Quiz App for disabled-selected in top 10 out of 650 participants in Hackathon conducted by Carestack",
      icon: "fa-solid fa-network-wired",
      description:
        "Track the status of network-connected devices in a clean mobile dashboard. Simple interface but powerful for IT admins to monitor uptime.",
      role: "Flutter Developer",
      imageUrl: "",
      tech: ["React", "Gemini-Api", "vercel"],
      year: "2024",
      links: {
        github:
          "https://github.com/bebialen/accessible-quiz-game/settings/access",
        web: "https://accessible-quiz-game.vercel.app/",
        demo: "https://accessible-quiz-game.vercel.app/",
      },
    },

    // https://accessible-quiz-game.vercel.app/
    {
      name: "Valet Parking App",
      tagline: "Vehicle entry & exit automation for parking staff",
      icon: "fa-solid fa-car-side",
      description:
        "Created for parking staff to track every vehicle entering or exiting their space. Designed the UI and implemented core features like quick scan, vehicle logs, and secure authentication.Still in development",
      role: "Android Developer",
      imageUrl: "",
      tech: [
        "Kotlin",
        "Jetpack Compose",
        "MVVM",
        "node",
        "Figma",
        "UI/UX",
        "MySQL",
      ],
      year: "2025",
      links: {
        github: "",
        playstore: "",
        web: "",
        demo: "",
      },
    },
    {
      name: "IP Device Monitoring App",
      tagline: "Monitoring network devices from your pocket",
      icon: "fa-solid fa-network-wired",
      description:
        "Track the status of network-connected devices in a clean mobile dashboard. Simple interface but powerful for IT admins to monitor uptime.",
      role: "Flutter Developer",
      imageUrl: "",
      tech: ["Flutter", "Provider", "node", "Figma", "UI/UX", "MySQL"],
      year: "2024",
      links: {
        github: "",
        playstore: "",
        web: "",
        demo: "",
      },
    },
  ];

  let benefits = [
    {
      name: "A Flutter Mobile App Developer",
      description:
        "Core expertise in Flutter using state management tools like Provider and BLoC, following clean architecture practices. I build smooth cross-platform apps with scalable code and great user experiences.",
    },
    {
      name: "Android + Frontend Experience",
      description:
        "Worked with Kotlin and Jetpack Compose for native Android, React and Angular for web — giving me the flexibility to ship apps across multiple platforms when needed.",
    },
    {
      name: "AI / ML — A Side Quest",
      description:
        "I have hands-on exposure to building ML models in Python using TensorFlow and basic data analysis tools. Not my main focus now, but a skill I can put to use when a project demands intelligence.",
    },
    {
      name: "Hobbies",
      description:
        "I love singing and composing music — creativity fuels my development style as well. Tech by day, musician by night.",
    },
  ];

  const profile = {
    name: "Alan Bebido",
    title: "Mobile App Developer",
    secondaryTitle: "(Android & iOS)",
    roles: [
      "Flutter Developer",
      "Android (Kotlin + Jetpack Compose)",
      "React & Angular Experience",
      "AI/ML — side quest",
    ],
    description:
      "I build cross-platform mobile apps with Flutter using Provider and BLoC. Worked with Kotlin for Android and React/Angular for the web.",
    favoriteTech: ["Flutter", "Kotlin", "BLoC", "Provider", "React", "Angular"],
    linkedin: "https://www.linkedin.com/in/alan-bebido-1934801b0/",
  };
</script>

<main class="flex flex-col flex-1 p-4">
  <section
    id="intropage"
    class="grid grid-cols-1 lg:grid-cols-2 gap-10 py-8 sm:py-14"
  >
    <div
      class="flex flex-col lg:justify-center text-center lg:text-left gap-6 md:gap-8
      lg:gap-10"
    >
      <h2 class="font-semibold text-4xl sm:text-5xl md text-6xl text-white">
        Hi! I’m <span class="text-violet-400">{profile.name}</span> <br />
        {profile.title}<span class="text-violet-400"
          >{profile.secondaryTitle}</span
        >
      </h2>

      <p class="text-base sm:text-lg md:text-xl text-white">
        I specialize in&nbsp;
        <span class="text-violet-400">{profile.favoriteTech.join(", ")}</span>
      </p>

      <a
        class="blueShadow mx-auto lg:mr-auto text-base sm:text-lg md:text-xl relative overflow-hidden
                px-6 py-3 group rounded-full bg-white text-slate-950 cursor-pointer"
        href={profile.linkedin}
        target="_blank"
      >
        <div
          class="absolute top-0 right-full w-full h-full bg-violet-400 opacity-20
      group-hover:translate-x-full z-0 duration-200"
        />
        <h4 class="relative z-9">Get in touch &rarr;</h4>
      </a>
    </div>

    <!-- <div class="relative shadow-2xl grid place-items-center">
      <div class="relative shadow-2xl grid place-items-center">
        <canvas
  bind:this={canvas}
  class="w-[350px] h-[350px] md:w-[450px] md:h-[450px] rounded-xl shadow-2xl mx-auto lg:mx-0"
/>

      </div>
    </div> -->


    <!-- //implement a img in here  -->
     <!-- <div class="relative shadow-2xl grid place-items-center">
                <img src={"/assets/images/profile_2.png"} alt="profile" class="object-cover z-[2] max-h[70vh]">
            </div> -->

    
  </section>
  //about me 
  <!-- <div 
  id="aboutMe" 
  class="text-3xl font-bold bg-gradient-to-r from-violet-400 to-fuchsia-500 bg-clip-text text-transparent"
>
  A Mobile App Developer with 1.7 years of experience building seamless Android & iOS experiences.
</div> -->

  <section id="projects" class="py-20 lg:py-32 flex flex-col gap-24">
    <div class="flex flex-col gap-2 text-center">
      <h6 class="text-large sm:text-xl md:text-2xl text-white">
        A few of my creative endeavours
      </h6>

      <h3 class="font -semibold texr-3xl sm:txt-4xl md:text-5xl text-white">
        Curious to <span class="text-violet-400">see</span> my work?
      </h3>
    </div>

    <section>
      <ProjectsCarousal {steps} />
    </section>

    <!-- <div class="grid grid-cols-1 lg:grid-cols-3 gap-10 lg:gap-10">
      {#each steps as step, i}
        //projects section
        <Step {step}>
          {#if step.tagline}
            <strong class="text-violet-400">{step.tagline}</strong>
          {/if}
        </Step>
      {/each}
    </div> -->
  </section>

  <!-- IMPLEMENT A BENTO BOX -->
  <section>
    <GitHubContrib />
  </section>
  <!-- PROFESSIONAL EXPERIENCE -->

  <section>
    <ProfessionalExperience />
  </section>

  <section
    id="about"
    class=" py-0 pt-10 lg:pt-16 lg:py-32 flex flex-col gap-16 sm:gap-20 md:gap-24 relative"
  >
    <div>
      <div class="flex flex-col gap-2 text-center relative">
        <!-- Subtitle -->
        <h6 class="text-7xl py-7 text-white">Want to Know more</h6>

        <!-- Main Heading with Typewriter Effect -->
        <h1 class="text-white text-4xl font-bold">
          <span
            class="poppins text-violet-700 sm:text-7xl inline-block overflow-hidden border-r-4 border-white whitespace-nowrap animate-typewriter"
          >
            A b o u t M e .. ??
          </span>
        </h1>
      </div>

      <!-- Tailwind Typewriter Animation -->
      <style>
        @keyframes typewriter {
          from {
            width: 0;
          }
          to {
            width: 100%;
          }
        }

        @keyframes blink {
          50% {
            border-color: transparent;
          }
        }

        .animate-typewriter {
          animation:
            typewriter 3s steps(30, end) 1s 1 normal both,
            blink 0.5s step-end infinite;
        }
      </style>
    </div>
    <p class="mx-auto font-christian font-semibold text-lg sm:text-4xl">
      Iam...
    </p>
    <div class="flex flex-col gap-20 w-full mx-auto max-w-[800px]">
      {#each benefits as benefit, index}
        <div class="flex gap-6 sm:gap-8">
          <p
            class="font-extrabold text-4xl text-7xl md:text-6l text-slate-500 font-semibold"
          >
            0{index + 1}
          </p>
          <div class="flex flex-col gap-6 sm:gap8">
            <h3
              class="text-2xl sm:text-3xl md:text-5xl font-semibold text-violet-400"
            >
              {benefit.name}
            </h3>
            <p class="text-slate-300">{benefit.description}</p>
          </div>
        </div>
      {/each}
    </div>
    <div>
      <div class="flex flex-col gap-0 text-center">
        <!-- Subtitle -->

        <!-- Main Heading with Typewriter Effect -->
        <h1 class="text-white font-bold">
          <span
            class="poppins text-violet-400 sm:text-2xl inline-block overflow-hidden border-r-4 border-white whitespace-nowrap animate-typewriter"
          >
            <code>&nbsp;--My Skills--&nbsp</code>
          </span>
        </h1>
      </div>
    </div>
    <Alert.Root>
      <Alert.Title>My skills</Alert.Title>

      <Alert.Description>
        <Alert.Root>
          <Alert.Title></Alert.Title>
          <Alert.Description>
            <div class="flex flex-wrap gap-3 text-center mt-5">
              <!-- Skill Pills -->
              <span
                class="px-4 py-2 text-white text-sm sm:text-md rounded-full border border-gradient-to-r from-emerald-400 via-emerald-500 to-emerald-600"
              >
                Flutter
              </span>
              <span
                class="px-4 py-2 text-white text-sm sm:text-md rounded-full border border-gradient-to-r from-emerald-400 via-emerald-500 to-emerald-600"
              >
                React
              </span>
              <span
                class="px-4 py-2 text-white text-sm sm:text-md rounded-full border border-gradient-to-r from-emerald-400 via-emerald-500 to-emerald-600"
              >
                Next.js
              </span>
              <span
                class="px-4 py-2 text-white text-sm sm:text-md rounded-full border border-gradient-to-r from-emerald-400 via-emerald-500 to-emerald-600"
              >
                MongoDB
              </span>
              <span
                class="px-4 py-2 text-white text-sm sm:text-md rounded-full border border-gradient-to-r from-emerald-400 via-emerald-500 to-emerald-600"
              >
                Node.js
              </span>
              <span
                class="px-4 py-2 text-white text-sm sm:text-md rounded-full border border-gradient-to-r from-emerald-400 via-emerald-500 to-emerald-600"
              >
                Machine Learning
              </span>
            </div>
          </Alert.Description>
        </Alert.Root>
      </Alert.Description>
    </Alert.Root>
  </section>
</main>
