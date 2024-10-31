<script lang="ts">
	import OsPageAboutMe from './OSPageAboutMe.svelte';
	import OsPageExperience from './OSPageExperience.svelte';
	import OsPageResume from './OSPageResume.svelte';

    interface Props {
        closePage: () => void
    }

    let { app, closePage }: { app: string, closePage: () => void} = $props();
</script>

<div class="page w-[85%] rounded-lg bg-[#17171c] border-black border-2 absolute left-1/2 top-7 -translate-x-1/2 z-10 shadow-xl flex flex-col overflow-hidden">
    <div id="tab" class="w-full h-16 bg-black flex flex-row-reverse items-center">
        <button id="close" class="h-full flex justify-center items-center" onclick={closePage}>
            X
        </button>
    </div>
    <div class="text-white overflow-auto">
        {#if app === 'aboutMe'}
        <OsPageAboutMe />
        {:else if app === 'experience'}
        <OsPageExperience/>
        {:else if app === 'resume'}
        <OsPageResume/>
        {/if}
    </div>
</div>

<style>
    .page{
        aspect-ratio: 4/3;
    }

    #close{
        height: 100%;
        aspect-ratio: 1/1;
        background: red;
        color: black;
    }

    /* width */
    ::-webkit-scrollbar {
        width: 15px;
    }

    /* Track */
    ::-webkit-scrollbar-track {
        background: transparent
    }

    /* Handle */
    ::-webkit-scrollbar-thumb {
        background-color: #aaaaaa2f;
        border-radius: 10px;
        transition: background-color 2s;
    }

    /* Handle on hover */
    ::-webkit-scrollbar-thumb:hover {
        background-color: #7a7a7aab;
    }
</style>