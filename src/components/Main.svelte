<script>
    import Step from "./Step.svelte"
    import * as Alert from "$lib/components/ui/alert";
    import { Motion } from 'svelte-motion';
	export let delay;

    let steps = [
        {name:'Clinical Management System', icon:'fa-regular fa-hospital'} ,
        {name:'OTT platform', icon:'fa-solid fa-clapperboard'} ,
        {name:'Blog App', icon:'fa-solid fa-users'} ,


    ]
let benefits = [
    {name:'A python-fullstack developer', 
    description:"Specializing in backend framework such as django coupled with relational databases such as mysql and sqlite and frontend frameworks like Angular and sveltekit"},
    {name:'A Data-scientist ', description:"Capable of analysing large datasets using python tools like numpy,pandas and visualising them using matplotlib.My datascience case studies include Econometrics, Entertainment, Healthcare, Human Resources, Insurance, Marketing/Sales, Retail, Sports"},
    {name:'A Machine learning /Deep Learning Engineer', description:"Implement Machine Learning and Deep Learning Algorithms using TensorFlow and Keras."},
    {name:'Hobbies', description:"Like to sing in free time, A musician/Composer in part time"}

]

</script>

<main class="flex flex-col flex-1 p-4">
    <section id='intropage' class="grid grid-cols-1 lg:grid-cols-2 gap-10 py-8 sm:py-14">
        <div class="flex flex-col lg:justify-center text-center lg:text-left gap-6 md:gap-8
        lg:gap-10">
            <h2 class="font-semibold text-4xl sm:text-5xl md text-6xl text-white ">
                Hi!Iam <span class="text-violet-400">
                    Alan </span>Bebido <br>Full stack 
                    <span class="text-violet-400">Developer</span> + <span class="text-violet-400">Data scientist</span>
                </h2>
                <p class="text-base sm:text-lg md:text-xl text-white">
                    My <span class="text-violet-400">favorite tech &nbsp;</span>includes Javascript (Angular and svelte), 
                    Bootstrap, Django+MySQl 
                </p>
                <a class="blueShadow mx-auto lg:mr-auto text-base sm:text-lg md:text-xl relative overflow-hidden
                px-6 py-3 group rounded-full bg-white text-slate-950 cursor-pointer" href="https://www.linkedin.com/in/alan-bebido-1934801b0/" target="_blank">
                <div class="absolute top-0 right-full w-full h-full bg-violet-400 opacity-20
    group-hover:translate-x-full z-0 duration-200"/>
                <h4 class="relative z-9">Get in touch &rarr;</h4>
            </a>
            </div>
            <div class="relative shadow-2xl grid place-items-center">
                <img src={"/assets/images/profile.png"} alt="profile" class="object-cover z-[2] max-h[70vh]">
            </div>

    </section>

    <section id='projects' class="py-20 lg:py-32 flex flex-col gap-24">
        <div class="flex flex-col gap-2 text-center">
            <h6 class="text-large sm:text-xl md:text-2xl text-white">
                A few of my creative endeavours
            </h6>
            <h3 class ="font -semibold texr-3xl sm:txt-4xl md:text-5xl text-white">
                Curious to <span class="text-violet-400">see</span> my work?

            </h3>

        </div>
       <!-- <div>
        <a href="#hello" target="_blank" class="mx-auto px-4 py-2 rounded-md border border-solid
        border-white flex items-center gap-2 -mb-4 sm:-mb-0 -mt-10 hover:border-violet-700
        duration-200">
        <i class="fa-regular fa-circle-play">
            <p>Watch the video</p>

        </i>
        
    </a>
       </div> -->
    <div class="grid grid-cols-1 lg:grid-cols-3 gap-10 lg:gap-10">
        
        <Step step={steps[0]}>
            <p>A Complete Clinical Management system </p>
            <strong class="text-violet-400">Collaboratively designed and developed a clinical management website using Angular as Frontend and Django as backend</strong>

        </Step>
        <Step step={steps[1]}>
            <p>A website to watch your favorite movies</p>
            <strong class="text-violet-400">Collaboratively designed and developed a comprehensive website using Django in which users can watch movies and TV
                series, add favorite movies or TV series to their watch list</strong>

        </Step>
        <Step step={steps[2]}>
            <p>A blog website for motorcycle enthusiasts </p>
            <strong class="text-violet-400">A website where you can post your favorite content on cars and bikes</strong>

        </Step>
   </div></section>

    <section id="about" class=" py-0 pt-10 lg:pt-16 lg:py-32 flex flex-col gap-16 sm:gap-20 md:gap-24 relative">

        
            <div>
                <div class="flex flex-col gap-2 text-center relative">
                    <!-- Subtitle -->
                    <h6 class="text-7xl py-7 text-white">Want to Know more</h6>
                    
                    <!-- Main Heading with Typewriter Effect -->
                    <h1 class="text-white text-4xl font-bold">
                      <span class="poppins text-violet-700 sm:text-7xl inline-block overflow-hidden border-r-4 border-white whitespace-nowrap animate-typewriter">
                        A b o u t  M e .. ??
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
                      animation: typewriter 3s steps(30, end) 1s 1 normal both, blink 0.5s step-end infinite;
                    }
                  </style>
                  
            </div>
            <p class="mx-auto font-christian  font-semibold text-lg sm:text-4xl">Iam...</p>
            <div class="flex flex-col gap-20 w-full mx-auto max-w-[800px]">
                {#each benefits as benefit, index}
                <div class="flex gap-6 sm:gap-8">
                    <p class="font-extrabold  text-4xl text-7xl md:text-6l text-slate-500 font-semibold">
                        0{index+1}
                    </p>
                    <div class="flex flex-col gap-6 sm:gap8">
                        <h3 class="text-2xl sm:text-3xl md:text-5xl font-semibold text-violet-400">
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
                        <h1 class="text-white  font-bold">
                          <span class="poppins text-violet-400 sm:text-2xl inline-block overflow-hidden border-r-4 border-white whitespace-nowrap animate-typewriter">
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
                                    <span class="px-4 py-2 text-white text-sm sm:text-md rounded-full border border-gradient-to-r from-emerald-400 via-emerald-500 to-emerald-600">
                                      Flutter
                                    </span>
                                    <span class="px-4 py-2 text-white text-sm sm:text-md rounded-full border border-gradient-to-r from-emerald-400 via-emerald-500 to-emerald-600">
                                      React
                                    </span>
                                    <span class="px-4 py-2 text-white text-sm sm:text-md rounded-full border border-gradient-to-r from-emerald-400 via-emerald-500 to-emerald-600">
                                      Next.js
                                    </span>
                                    <span class="px-4 py-2 text-white text-sm sm:text-md rounded-full border border-gradient-to-r from-emerald-400 via-emerald-500 to-emerald-600">
                                      MongoDB
                                    </span>
                                    <span class="px-4 py-2 text-white text-sm sm:text-md rounded-full border border-gradient-to-r from-emerald-400 via-emerald-500 to-emerald-600">
                                      Node.js
                                    </span>
                                    <span class="px-4 py-2 text-white text-sm sm:text-md rounded-full border border-gradient-to-r from-emerald-400 via-emerald-500 to-emerald-600">
                                      Machine Learning
                                    </span>
                                  </div>
                            </Alert.Description>
                        </Alert.Root>
                    </Alert.Description>
                </Alert.Root>
                
            </section>
   
            
    
</main>