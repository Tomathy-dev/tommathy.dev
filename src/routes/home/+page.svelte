<script lang="ts">
	import OsPage from '$lib/OSPage.svelte';
import Runes from '$lib/Runes.svelte';
	import { onMount } from "svelte";

    type App = 'aboutMe' | 'experience' | 'resume' | 'none'

    let TomSay: string = $state("")
    let app: App = $state('none')
    const deleteSpeed: number = 50 //ms
    let timeouts: number[] = []

    function removeTimeouts(){
        for(let i = 0; i < timeouts.length; i++){
            clearTimeout(timeouts[i])
        }
        timeouts = []
    }

    function insertTomSay(text: string){
        let offset: number = 0
        if(TomSay.length !== 0){
            offset = removeTomSay() //setTimeouts are async, so it needs o wait for removal with offset
        }
        for(let i = 0; i < text.length; i++){
            timeouts.push(setTimeout(() => {
                TomSay = TomSay.concat(text.charAt(i))
            }, (offset * deleteSpeed) + (100 * i)))
        }
    }

    function removeTomSay(): number{
        if(TomSay.length === 0) return 0
        const og_length = TomSay.length
        for(let i = 0; i < og_length; i++){
            timeouts.push(setTimeout(() => {
            TomSay = TomSay.slice(0, -1)
            }, deleteSpeed * i))
        }
        return og_length
    }

    onMount(() => {
        timeouts.push(setTimeout(() => {
            insertTomSay("Welcome!")
        }, 1000))
        timeouts.push(setTimeout(() => {
            insertTomSay("Double click the apps!")
        }, 3000))
        timeouts.push(setTimeout(() => {
            removeTimeouts()
        }, 7000))
    })
</script>

<div id="window" class="w-full h-full relative">
    <Runes />
    <div class="TomBody">
        <p class="absolute top-[-20px] max-h-[1px] flex flex-col-reverse text-center flex-grow">{TomSay}</p>
        <div class="TomEye">
            <div class="TomIris"></div>
        </div>
    </div>
    <div class="TomShadow"></div>
    <div class="w-full h-full flex flex-col absolute">
        <div id="apps" class="w-full grow p-7 gap-2 flex flex-col ">
            <button class=" w-32 h-32 gap-2 flex flex-col flex-none items-center justify-center" ondblclick={() => app = 'aboutMe'}>
                <img src="AboutMe.svg" alt="About me icon" width="64px">
                <label for="About Me">About Me</label>
            </button>
            <button class=" w-32 h-32 gap-2 flex flex-col flex-none items-center justify-center" ondblclick={() => app = 'experience'}>
                <img src="Experience.svg" alt="Experience icon" width="64px">
                <label for="Experience">Experience</label>
            </button>
            <button class=" w-32 h-32 gap-2 flex flex-col flex-none items-center justify-center" ondblclick={() => app = 'resume'}>
                <img src="Resume.svg" alt="Resume icon" width="64px">
                <label for="Resume">Resume<br/>.pdf</label>
            </button>
        </div>
        <button class=" w-32 h-32 gap-2 flex flex-col flex-none items-center justify-center absolute right-7 top-7">
            <img src="WIP.svg" alt="Work in Progress icon" width="64px">
            <label for="WIP">WIP</label>
        </button>
        {#if app === 'aboutMe'}
            <OsPage {app} closePage={() => app = 'none'} />
        {:else if app === 'experience'}
            <OsPage {app} closePage={() => app = 'none'} />
        {:else if app === 'resume'}
            <OsPage {app} closePage={() => app = 'none'} />
        {/if}
        <div id="toolbar" class="w-full h-12 bg-black z-20"></div>
    </div>

</div>

<style>
    #window {   
        overflow: hidden;
        background: rgb(20, 20, 20);
        font-family: "Press Start", sans-serif;
        font-weight: 400;
        font-size: 0.8em;
        font-style: normal;
    }

    button:hover{
        background-color: rgba(255, 255, 255, 0.1);
    }

    button{
        border-radius: 10px;
    }

    .TomBody{
        width: 20%;
        aspect-ratio: 1/1;
        right: 50px;
        background: rgb(0, 0, 0);
        border-radius: 50%;
        position: absolute;
        display: flex;
        justify-content: center;
        align-items: center;
        animation: hover 4s infinite ease-in-out;
    }

    .TomEye{
        width: 55%;
        aspect-ratio: 1/1;
        background: rgb(255, 255, 255);
        border-radius: 0 90% 0 90%;
        position: relative;
        display: flex;
        justify-content: center;
        align-items: center;
        transform: rotate(-45deg);
        overflow: hidden;
        animation: blink 7s infinite;
    }

    .TomIris{
        width: 45%;
        aspect-ratio: 1/1;
        background:rgb(0, 0, 0);
        border-radius: 50%;
    }

    .TomShadow{
        width: 20%;
        aspect-ratio: 20/3;
        filter: blur(3px);  
        border-radius: 100%;
        background: rgb(0, 0, 0, 0.3);
        position: absolute;
        bottom: 60px;
        right: 50px;
        transform-origin: center;
        animation: scale 4s infinite ease-in-out;
    }

    @keyframes blink{
        0%{
            opacity: 100%;
        }
        99%{
            opacity: 100%;
        }
        100%{
            opacity: 0%;
        }
    }

    @keyframes hover{
        0%, 100%{
            bottom: 140px;
        }
        50%{
            bottom: 110px;
        }
    }

    @keyframes scale{
        0%, 100%{
            transform: scale(0.8)
        }
        50%{
            transform: scale(1)
        }
    }
</style>