<script>
    import Navlink from "../lib/Navlink.svelte";
</script>

<Navlink />

<!-- tailwind container center -->
<div class="container mx-auto">
    <div class="grid md:grid-cols-2 m-auto md:w-3/4 gap-3 md:gap-6">
        <a href="/">
            <div
                class="flex justify-center items-center w-50 md:py-9 border rounded hover:bg-gray-900 hover:text-white cursor-pointer"
            >
                Home
            </div>
        </a>
        <a href="/layout">
            <div
                class="flex justify-center items-center w-50 md:py-9 border rounded hover:bg-gray-900 hover:text-white cursor-pointer"
            >
                Layout
            </div>
        </a>
        <a href="/chart">
            <div
                class="flex justify-center items-center w-50 md:py-9 border rounded hover:bg-gray-900 hover:text-white cursor-pointer"
            >
                Chart
            </div>
        </a>
        <a href="/map">
            <div
                class="flex justify-center items-center w-50 md:py-9 border rounded hover:bg-gray-900 hover:text-white cursor-pointer"
            >
                Map
            </div>
        </a>
    </div>
</div>
