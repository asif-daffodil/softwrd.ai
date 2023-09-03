<script>
    import { page } from "$app/stores";
    $: activeUrl = $page.url.pathname;
</script>

<!-- svelte if condition -->    


<header class="text-gray-600 body-font">
    <div
        class="container mx-auto flex flex-wrap p-5 flex-col md:flex-row items-center"
    >
        <nav
            class="md:ml-auto md:mr-auto flex flex-wrap items-center text-base justify-center"
        >
            <a
                href="/"
                class="mr-3 md:mr-5 hover:text-gray-400 {activeUrl == '/'
                    ? 'font-bold'
                    : null}"
            >
                Home
            </a>
            <a
                href="/layout"
                class="mr-3 md:mr-5 hover:text-gray-400 {activeUrl == '/layout'
                    ? 'font-bold'
                    : null}"
            >
                Layout
            </a>
            <a
                href="/chart"
                class="mr-3 md:mr-5 hover:text-gray-400 {activeUrl == '/chart'
                    ? 'font-bold'
                    : null}"
            >
                Chart
            </a>
            <a
                href="/map"
                class="md:mr-5 hover:text-gray-400 {activeUrl == '/map'
                    ? 'font-bold'
                    : null}"
            >
                Map
            </a>
        </nav>
    </div>
</header>
