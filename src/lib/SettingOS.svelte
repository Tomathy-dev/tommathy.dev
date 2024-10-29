<script lang="ts">
	import { onMount } from "svelte";
    import { OStext } from "./OStext";

    let OS: string[] = $state([]);
    const duration = 100;
    let logState = $state("paused");
    let { stateLogo }: { stateLogo: () => void }= $props();

    function textAppear(node: HTMLElement, { from, to }: { from: DOMRect; to: DOMRect }, params?: any ) {
        if(node.parentElement) node.parentElement.scrollTo(0, node.parentElement.scrollHeight);
        return{
            delay: 0,
            duration: duration,
            css: (t: number) => `width: ${t * 100}%; overflow: hidden;`
        }
    };

    function addOSText() {
        for (let i = 0; i < OStext.length; i++) {
            setTimeout(() => {
                OS = [...OS, OStext[i]];
            }, duration * i);
        }
    }

    $effect(() => {
        if (OS.length === OStext.length) {
            setTimeout(() => {
                stateLogo();
            }, duration * 10);
        }
    });

    $inspect(OS)

    onMount(() => {
        setTimeout(() => {
            logState = "running";
            addOSText()
        }, 2000);
    });
</script>

<div id="container" class="w-full h-full overflow-y-auto">
    {#if logState === "running"}
        {#each OS as item}
            <p transition:textAppear>{item}</p>
        {/each}
    {/if}
    <div id="cursor" class="h-5 w-5"></div>
</div>

<style>
    p {
        overflow: hidden;
        height: 1.3em;
        animation: jerk 50ms infinite;
    }

    #container{
        padding: 30px;
        background: radial-gradient(circle at 50% 50%, rgb(10, 10, 10), black);
    }

    #cursor {
        animation: blink 1s infinite;
        flex: auto;
        flex-flow: column-reverse;
    }

    #cursor::before {
        content: "";
        display: inline-block;
        width: 1.2em;
        height: 3px;
        background-color: #dddd;
    }

    @keyframes jerk {
        50%{
            transform: translateX(-1px);
        }
        51%{
            transform: translateX(0px);
        }
    }

    @keyframes blink {
        0%{
            opacity: 1;
        }
        49%{
            opacity: 1;
        }
        50%{
            opacity: 0;
        }
        100%{
            opacity: 0;
        }
    }

    /* width */
    #container::-webkit-scrollbar {
        width: 10px;
    }

    /* Track */
    #container::-webkit-scrollbar-track {
        background: transparent
    }

    /* Handle */
    #container::-webkit-scrollbar-thumb {
        background: #aaaaaa2f;
        border-radius: 5px;
    }

    /* Handle on hover */
    #container::-webkit-scrollbar-thumb:hover {
        background: #4949498a;
    }
</style>