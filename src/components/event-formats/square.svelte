<script>
    export let event;
    export let image;
    export let tools;
</script>


<div id="img-square" class="aspect-square w-[400px] relative bg-black text-white overflow-hidden">
    <img src="/logo.svg" class="absolute top-8 left-8 w-1/2 z-20" />

    <div class="absolute top-0 left-0 h-36 w-full z-10" style="background: linear-gradient(black, transparent);"></div>
    <div class="absolute top-0 left-0 h-full w-1/2 z-10" style="background: linear-gradient(to left, transparent, black);"></div>
    <img src={image.src} class="absolute top-0 left-0 -z-0 h-full object-cover" style="{image.calcObjOffsets('square')}" />


    {#if event.type === 'summit'}
        <img src="/gen-img/summit-title3.svg" class="absolute -bottom-1 left-0 w-full z-20" />
        <div class="absolute bottom-0 left-0 h-32 w-full z-10" style="background: linear-gradient(transparent, black);"></div>

        <div class="absolute bottom-20 left-8 right-8 uppercase text-[2rem] z-20 font-kyiv">
            <div>
                {tools.dateFormat(event.date, "dd/MM/yyyy")}
            </div>
            <div class="-mt-1">
                {event.city}
            </div>
        </div>
    {:else}
        <div class="absolute bottom-8 left-8 uppercase z-20">
            <div class="flex">
                <div class="border-2 border-white py-1 px-2 border-r-0 inline-block bg-black">
                    {tools.dateFormat(event.date)}
                </div>
                <div class="border-2 border-white py-1 px-2 bg-black">
                    {event.city}, {event.country}
                </div>
            </div>
            <div class="flex">
                <div class="border-2 border-white py-1 px-2 bg-white text-black uppercase">
                    {event.type}
                </div>  
            </div>
        </div>
    {/if}
</div>