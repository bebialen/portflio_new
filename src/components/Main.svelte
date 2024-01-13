<script>
    import Step from "./Step.svelte"
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
            <h2 class="font-semibold text-4xl sm:text-5xl md text-6xl ">
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
            <h6 class="text-large sm:text-xl md:text-2xl">
                A few of my creative endeavours
            </h6>
            <h3 class ="font -semibold texr-3xl sm:txt-4xl md:text-5xl">
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
    <div class="grid grid-cols-1 lg:grid-cols-3 gap-12 lg:gap-10">
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

    <section id="about" class="py-20 pt-10 lg:pt-16 lg:py-32 flex flex-col gap-16 sm:gap-20 md:gap-24 relative">
            <div class="flex flex-col gap-2 text-center relative  before:absolute before:top-0 before:left-0  before:w-2/3 before:h-1.5 before:bg-violet-700 after:absolute after:bottom-0 after:right-0 after:bottom-0 after:right-0 after:w-2/3 after:h-1.5 after:bg-violet-700 py-4">
            <h6 class="text-lg sm:text-xl md:text-2xl text-white">Want to Know more</h6>
            <h3 class="">A bit <span class="poppins text-violet-400">about</span> me ??</h3>
            </div>
            <p class="mx-auto font-christian  font-semibold text-lg sm:text-4xl">Iam...</p>
            <div class="flex flex-col gap-20 w-full mx-auto max-w-[800px]">
                {#each benefits as benefit, index}
                <div class="flex gap-6 sm:gap-8">
                    <p class="font-christian text-4xl sm:text-5xl md:text-6l text-slate-500 font-semibold">
                        0{index+1}
                    </p>
                    <div class="flex flex-col gap-6 sm:gap8">
                        <h3 class="text-2xl sm:text-3xl md:text-5xl">
                            {benefit.name}
                        </h3>
                        <p>{benefit.description}</p>
    
                    </div>
                    
                </div>
                {/each}
                </div>
                <h5 class="text-white ">The <span class ='text-violet-400'>Complete</span> Package of my Skills &nbsp;<i class="fa-solid fa-cloud-bolt text-violet-200"></i></h5>
                <div class="flex flex-col overflow-x-scroll gap-10 max-w-[800px] mx-auto w-full">
                    <table class="bg-white text-slate-700 rounded text-center">
                        <thead class="border-b border-solid border-slate-200 ">
                            <tr class="">
                                <th class="whitespace-nowrap p-2 px-4 text-lg  text-black">Domain</th>
                                <th class="whitespace-nowrap p-2 px-4 text-lg text-black">Technologies</th>


                            </tr>
                        </thead>
                        <tbody>
                            <tr class="border-b border-solid border-slate-200">
                                <td class="border-r border-solid border-white pl-4 pr-8 py-4 font-christian font-bold text-sm">Fullstack Web development</td>
                                <td class="border-r border-solid border-white pl-4 pr-8 py-4 font-poppins text-xs text-blue-400">Django with restAPI,Angular</td>

                                <td></td>
    
                            </tr>
                        </tbody>
                        <tbody>
                            <tr class="border-b border-solid border-slate-200">
                                <td class="border-r border-solid border-white pl-4 pr-8 py-4 font-christian font-bold text-sm">Data Science</td>
                                <td class="border-r border-solid border-white pl-4 pr-8 py-4 font-poppins text-xs text-blue-400">Pandas, numpy, Matplotlib, Seaborn,sciKit Learn</td>

                                <td></td>
    
                            </tr>
                        </tbody>
                        <tbody>
                            <tr class="border-b border-solid border-slate-200">
                                <td class="border-r border-solid border-white pl-4 pr-8 py-4 font-christian font-bold text-sm">ML and Deep Learning</td>
                                <td class="border-r border-solid border-white pl-4 pr-8 py-4 font-poppins text-xs text-blue-400">Keras library</td>

                                <td></td>
    
                            </tr>
                        </tbody>
                        <tbody>
                            <tr class="border-b border-solid border-slate-200">
                                <td class="border-r border-solid border-white pl-4 pr-8 py-4 font-christian font-bold text-sm">Extras</td>
                                <td class="border-r border-solid border-white pl-4 pr-8 py-4 font-poppins text-xs text-blue-400 ">Web scraping with scrapy, Version control systems like Git and GitHub</td>

                                <td></td>
    
                            </tr>
                        </tbody>
                    </table>
                    
                </div>
            </section>
   
            
    
</main>