<script>
    import { fly } from "svelte/transition";
</script>
<!-- tailwind container middle -->
<div class="container mx-auto grid min-h-screen md:grid-cols-2 overflow-hidden" transition:fly={{x:200}}>
    <div class="grid">
        <div
            class="md:col-span-2 md:row-span-3 bg-blue-400 min-h-[320px] md:min-h-[auto]"
        />
        <div
            class="md:col-span-4 md:row-span-5 bg-rose-100 min-h-[320px] md:min-h-[auto]"
        />
        <div
            class="md:col-span-2 md:row-span-2 bg-teal-400 min-h-[320px] md:min-h-[auto]"
        />
        <div
            class="md:col-span-6 md:row-span-1 bg-fuchsia-400 min-h-[320px] md:min-h-[auto]"
        />
    </div>
    <div class="grid">
        <div
            class="md:col-span-6 md:row-span-2 bg-blue-400 min-h-[320px] md:min-h-[auto]"
        />
        <div
            class="md:col-span-4 md:row-span-4 bg-yellow-100 flex min-h-[320px] md:min-h-[auto]"
        >
            <div class="m-auto flex w-[300px] h-[300px] bg-[#293462]">
                <div
                    class="inner-circle m-auto flex w-[200px] h-[200px] bg-[#fef9c3] rounded-full overflow-hidden"
                >
                    <div class="hills m-auto w-full h-full bg-[#fe5f55]" />
                </div>
            </div>
        </div>
        <div
            class="md:col-span-2 md:row-span-4 bg-emerald-400 min-h-[320px] md:min-h-[auto]"
        />
    </div>
</div>

<style>
    .hills {
        clip-path: polygon(
            0% 100%,
            0% 80%,
            20% 60%,
            30% 70%,
            70% 30%,
            100% 70%,
            100% 100%
        );
    }
</style>
