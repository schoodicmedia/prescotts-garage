<script lang="ts">
    import { scrollRef } from "svelte-scroll-nav";
    import Image from "./Image.svelte";

    export let image: {
        src: string;
        alt: string;
    } | undefined = undefined;
    export let heading: string | undefined = undefined;

    let scrollRefName: string | undefined = undefined;
    export { scrollRefName as scrollRef };
</script>
<section use:scrollRef={scrollRefName} class="section">
    <div class="flex flex-col lg:flex-row gap-12 max-w-[1000px] m-auto lg:items-center">
        {#if image}
            <div class="section-image">
                <Image src={image.src} alt={image.alt} aspect="10:9" width="100%"/>
            </div>
        {/if}
        <div class="flex flex-col gap-4">
            {#if heading}
                <h2 class="font-poppins text-3xl sm:text-4xl lg:text-5xl font-bold text-center">
                    { heading }
                </h2>
            {/if}
            <slot />
        </div>
    </div>
</section>