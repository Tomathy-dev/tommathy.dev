<script lang="ts">
	import LogoIntro from "$lib/LogoIntro.svelte";
import SettingOs from "$lib/SettingOS.svelte";
import { onMount } from "svelte";

type State = "running" | "paused" | "logo";

let pageState: State = $state("paused");

function stateLogo() {
    pageState = "logo";
}

onMount(() => {
    setTimeout(() => {
        pageState = "running";
    }, 200);
});

$inspect(pageState);

</script>

<div class="w-full h-full">
    {#if pageState === "running"}
        <SettingOs stateLogo={stateLogo} />
    {:else if pageState === "logo"}
        <LogoIntro />
    {/if}
</div>