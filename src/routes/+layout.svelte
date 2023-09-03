<script>
  import "../app.css";
    import Navlink from "../lib/Navlink.svelte";
    import { page } from "$app/stores";
    $: activeUrl = $page.url.pathname;
</script>
{#if activeUrl != '/chart'}
<Navlink />
{/if}
<slot />