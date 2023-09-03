<script>
    import { fly } from "svelte/transition";
</script>

<!-- tailwind container center -->
<div class="container mx-auto overflow-hidden" transition:fly={{x:200}} >
    <div class="grid md:grid-cols-2 m-auto md:w-3/4">
        <a href="/">
            <div
                class="flex justify-center items-center w-50 md:py-9 border bg-[#f65314] hover:bg-gray-900 text-white cursor-pointer"
            >
                Home
            </div>
        </a>
        <a href="/layout">
            <div
                class="flex justify-center items-center w-50 md:py-9 border bg-[#7cbb00] hover:bg-gray-900 text-white cursor-pointer"
            >
                Layout
            </div>
        </a>
        <a href="/chart">
            <div
                class="flex justify-center items-center w-50 md:py-9 border bg-[#00a1f1] hover:bg-gray-900 text-white cursor-pointer"
            >
                Chart
            </div>
        </a>
        <a href="/map">
            <div
                class="flex justify-center items-center w-50 md:py-9 border bg-[#ffbb00] hover:bg-gray-900 text-white cursor-pointer"
            >
                Map
            </div>
        </a>
    </div>
</div>
