<script>
    import { onMount } from "svelte";
    import Chart from "chart.js/auto";
    import { countryDataStore } from "../../countryDataStore";

    let top10PopulatedCountries = [];

    onMount(() => {
        const ctx = document.getElementById("populationChart").getContext("2d");

        // Fetch data from the API if it hasn't been fetched yet
        countryDataStore.subscribe((data) => {
            // Check if data is available and not empty
            if (data && data.length > 0) {
                // Sort the data by population in descending order
                data.sort((a, b) => b.population - a.population);

                // Get the top 10 populated countries
                top10PopulatedCountries = data.slice(0, 10);

                // Update the chart
                const chartData = {
                    labels: top10PopulatedCountries.map(
                        (country) => country.name.common
                    ),
                    datasets: [
                        {
                            label: "Population (millions)",
                            data: top10PopulatedCountries.map(
                                (country) => country.population
                            ),
                            backgroundColor: [
                                "rgba(255, 99, 132, 0.5)",
                                "rgba(54, 162, 235, 0.5)",
                                "rgba(255, 206, 86, 0.5)",
                                "rgba(75, 192, 192, 0.5)",
                                "rgba(153, 102, 255, 0.5)",
                                // Add more colors as needed
                            ],
                            hoverOffset: 4,
                        },
                    ],
                };

                const populationChart = new Chart(ctx, {
                    type: "polarArea",
                    data: chartData,
                });
            }
        });
    });
</script>

<canvas id="populationChart" />

<!-- Display the top 10 populated countries -->
<div>
    <h2 class="text-center">Top 10 Populated Countries</h2>
</div>
