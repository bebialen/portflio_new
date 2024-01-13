<script>
    export let y;
    let tabs = [
        { name: 'Projects', link: '#projects' },
        { name: 'About me', link: '#about' },
        ];
</script>

<header class={"sticky z-[10] top-0 duration-200 px-6 flex items-center justify-between border border-solid" +
 (y>0? "py-4 bg-slate-950 border-violet-950" : "py-6 bg-transparent border-transparent")
}>
    <h1 class="font-medium">
        <b class="font-bold poppins text-white opacity-80 text-xl">Alan</b></h1>
    <div class="sm:flex items-center gap-4 hidden font-bold  ">
        {#each tabs as tab}
            <a href={tab.link} class="duration-200 hover:text-violet-400 ">
                <p>{tab.name}</p>
            </a>
        {/each}
    </div>
    <a class="blueShadow relative overflow-hidden px-5 py-1 group rounded-full bg-white 
    text-slate-950 top-1" href="https://www.linkedin.com/in/alan-bebido-1934801b0/" target="_blank">
    <div class="absolute top-0 right-full w-full h-full bg-violet-400 opacity-20
    group-hover:translate-x-full z-0 duration-200"></div>
    <h4 class="relative z-9 ">Get in touch</h4>

</header>

