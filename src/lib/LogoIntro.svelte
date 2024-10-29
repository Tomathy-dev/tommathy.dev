<script lang="ts">
	import { onMount } from "svelte";

    let pressableKeys: boolean = $state(false)

    $effect(() => {
        if(pressableKeys){
            window.addEventListener("keydown", () => {
                window.location.href = "/home"
            })
            window.addEventListener("click", () => {
                window.location.href = "/home"
            })
        }
    })

    onMount(() => {
        setTimeout(() => {
            pressableKeys = true
        }, 7000)
    })
</script>

<div id="window" class="w-full h-full flex items-center justify-center flex-col relative">
    <div class="image-wrapper w-1/2 h-1/4 relative">
        <img src="TommathyOS.svg" alt="TommathyOS" class="logo w-full h-auto absolute z-10" />
        <img src="TommathyOSRed.svg" alt="TommathyOS" class="logo w-full h-auto absolute" />
        <img src="TommathyOSBlue.svg" alt="TommathyOS" class="logo w-full h-auto absolute" />
    </div>
    {#if !pressableKeys}
    <div class="loader-border w-1/2 h-8 border-4 border-[#dddd] p-2">
        <div class="loader w-full h-full bg-[#dddd]"></div>
    </div>
    {:else}
        <div class="w-1/2 h-8 flex items-center justify-around">
            <p>[</p>
            <p>Press any key to start</p>
            <p>]</p>
        </div>
    {/if}
</div>

<style>
    #window {
        overflow: hidden;
        background: radial-gradient(circle at 50% 50%, rgb(10, 10, 10), black);
        padding: 50px;
    }

    .loader-border{
        animation: fadeIn 2s 1s backwards;
    }

    .loader {
        animation: load 2s 3s backwards;
    }

    .image-wrapper {
        animation: fadeIn 2s 1s backwards, jerkwhole 5s 3s infinite;
    }

    .image-wrapper img:nth-child(2){
        transform: translateX(-3px);
        animation: jitterRed 6s infinite;
    }

    .image-wrapper img:nth-child(3){
        transform: translateX(3px);
        animation: jitterBlue 3s infinite;
    }

    .image-wrapper img{
        animation: jitter 50ms infinite;
    }

    @keyframes load {
        0% {
            width: 0;
        }
        9%{
            width: 0%;
        }
        10%{
            width: 10%;
        }
        25%{
            width: 25%;
        }
        50% {
            width: 35%;
        }
        75% {
            width: 50%;
        }
        90% {
            width: 75%;
        }
        95% {
            width: 99%;
        }
        100% {
            width: 100%;
        }
    }

    @keyframes jitterRed {
        0%{
            transform: translateX(-3px);
        }
        30%{
            transform: translateX(-3px);
        }
        31%{
            transform: translate(-10px, -3px);
        }
        32%{
            transform: translateX(-3px);
        }
        99%{
            transform: translateX(-3px);
        }
        100%{
            transform: translate(7px, 7px);
        }
    }

    @keyframes jitterBlue {
        0%{
            transform: translateX(3px);
        }
        40%{
            transform: translateX(3px);
        }
        41%{
            transform: translate(8px, 3px);
        }
        42%{
            transform: translateX(3px);
        }
        99%{
            transform: translateX(3px);
        }
        100%{
            transform: translate(12px, -7px);
        }
    }

    @keyframes jitter {
        50%{
            transform: translateX(-1px);
        }
        51%{
            transform: translateX(0px);
        }
    }

    @keyframes fadeIn {
        0% {
            opacity: 0;
        }
        24%{
            opacity: 0;
        }
        25% {
            opacity: 0.25;
        }
        49%{
            opacity: 0.25;
        }
        50% {
            opacity: 0.5;
        }
        74%{
            opacity: 0.5;
        }
        75% {
            opacity: 0.75;
        }
        99%{
            opacity: 0.75;
        }
        100% {
            opacity: 1;
        }
    }

    @keyframes jerkwhole {
    30% {  }
    40% { opacity:1; transform:scale(1,1); transform:skew(0,0);}
    41% { opacity:0.8; transform:scale(1,1.1); transform:skew(50deg,0deg);}
    42% { opacity:0.8; transform:scale(1,0.8); transform:skew(-30deg,0deg);}
    43% { opacity:1; transform:scale(1,1); transform:skew(0,0);}
    65% { }
  }
</style>