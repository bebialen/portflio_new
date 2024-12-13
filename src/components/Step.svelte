<script>
    export let step;
    import { Button } from "$lib/components/ui/button";
</script>

<a
    href={step.href}
    target="_blank"
    class="p-4 sm:p-6 md:p-8 flex flex-col
gap-4 rounded-lg border border-solid border-violet-700 text-center group cursor-pointer hover:border-violet-400 duration-200"
>
    <div
        class="bg-slate-950 grid place-items-center px-4 text-5xl md:text-6xl-mt-10
sm:-mt-12 md:-mt-14 lg:-mt-16 mx-auto duration-200 text-slate-300"
    >
        <i class={step.icon} />
    </div>
    <h3 class="font-medium text-xl sm:text-2xl md:text-3xl text-violet-50">{step.name}</h3>
    <slot />
    <div class="flex justify-center items-center gap-6">
        <!-- Button 1 -->
        <div class="cursor-pointer relative group">
            <a
                href="https://github.com/bebialen/Playstream.git"
                target="_blank"
                class="flex items-center gap-2 px-4 py-2 border-violet-300 text-violet-700 font-semibold rounded-lg hover:bg-violet-700 hover:text-white duration-300"
            >
                <!-- GitHub Icon -->
                <div>
                    <Button variant="outline">
                        <p>Take me</p>
                    </Button>
                </div>
            </a>
        </div>

        <!-- Button 2 -->
        <div class="cursor-pointer relative group">
            <a
                href="https://github.com/bebialen/Playstream.git"
                target="_blank"
                class="flex items-center gap-2 px-4 py-2 text-violet-700 font-semibold rounded-lg hover:bg-violet-700 hover:text-white duration-300"
            >
                <div>
                    <Button variant="outline">
                        <i class="fa-brands fa-github text-2xl">&nbsp;</i>
                        <p> GitHub</p>
                    </Button>
                </div>
            </a>
        </div>
    </div>
</a>
