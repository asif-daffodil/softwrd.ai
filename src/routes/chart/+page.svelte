<script>
    import { afterUpdate } from "svelte";
    import { countryDataStore } from "../../countryDataStore";
    import PopulationChart from "../../lib/PopulationChart.svelte";
    afterUpdate(async () => {
        // Fetch data from the API if it hasn't been fetched yet
        const response = await fetch("https://restcountries.com/v3.1/all");
        const data = await response.json();

        // Store the data in countryDataStore
        countryDataStore.set(data);
    });
</script>

<div class="container m-auto">
    <header class="text-gray-600 body-font">
        <div
            class="container mx-auto flex flex-wrap p-5 flex-col md:flex-row items-center"
        >
            <nav
                class="md:ml-auto md:mr-auto flex flex-wrap items-center text-base justify-center"
            >
                <!-- svelte-ignore a11y-click-events-have-key-events -->
                <!-- svelte-ignore a11y-no-static-element-interactions -->
                <div
                    on:click={() => {
                        location.href = "/";
                    }}
                    class="mr-3 md:mr-5 hover:text-gray-400 cursor-pointer"
                >
                    Home
                </div>
                <!-- svelte-ignore a11y-click-events-have-key-events -->
                <!-- svelte-ignore a11y-no-static-element-interactions -->
                <div
                    on:click={() => {
                        location.href = "/layout";
                    }}
                    class="mr-3 md:mr-5 hover:text-gray-400 cursor-pointer"
                >
                    Layout
                </div>
                <!-- svelte-ignore a11y-click-events-have-key-events -->
                <!-- svelte-ignore a11y-no-static-element-interactions -->
                <div
                    on:click={() => {
                        location.href = "/chart";
                    }}
                    class="mr-3 md:mr-5 hover:text-gray-400 cursor-pointer font-bold"
                >
                    Chart
                </div>
                <!-- svelte-ignore a11y-click-events-have-key-events -->
                <!-- svelte-ignore a11y-no-static-element-interactions -->
                <div
                    on:click={() => {
                        location.href = "/map";
                    }}
                    class="md:mr-5 hover:text-gray-400 cursor-pointer"
                >
                    Map
                </div>
            </nav>
        </div>
    </header>

    <div class="grid grid-cols-12">
        <div class="md:col-span-8">
            <table
                class="min-w-full devide-x divide-y divide-gray-200 border border-gray-300"
            >
                <thead>
                    <tr class="divide-x divide-y divide-gray-200">
                        <th
                            class="p-1 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
                            >Flag</th
                        >
                        <th
                            class="p-1 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
                            >Name</th
                        >
                        <th
                            class="p-1 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
                            >CIOC</th
                        >
                        <th
                            class="p-1 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
                            >UN Member Status</th
                        >
                        <th
                            class="p-1 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
                            >Currencies (Key)</th
                        >
                        <th
                            class="p-1 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
                            >Population</th
                        >
                        <th
                            class=" bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
                            >Languages</th
                        >
                    </tr>
                </thead>
                <tbody>
                    {#each $countryDataStore as country}
                        <tr class=" border border-gray-300">
                            <td class="p-1"
                                ><img
                                    src={country.flags.png}
                                    alt={country.name.common}
                                    class="h-9 w-9 rounded-full"
                                /></td
                            >
                            <td class="p-1">{country.name.common}</td>
                            <td class="p-1">{country.cioc}</td>
                            <td class="">{country.unMember ? "Yes" : "No"}</td>
                            <td class="p-1"
                                >{Object?.keys(country?.currencies).join(
                                    ", "
                                )}</td
                            >
                            <td class="p-1">{country.population}</td>
                            <td class="p-1"
                                >{Object.values(country.languages).join(
                                    ", "
                                )}</td
                            >
                        </tr>
                    {/each}
                </tbody>
            </table>
        </div>
        <div class="md:col-span-4">
            <PopulationChart />
        </div>
    </div>
</div>
