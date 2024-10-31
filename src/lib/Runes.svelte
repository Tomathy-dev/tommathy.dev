<script lang="ts">
	import { onMount } from "svelte";
	import type { Action } from "svelte/action";


type Rune = {
    character: string,
    x: number,
    size: number,
    color: string
}

const possibleRunes: string = "Dqwertyuiopasdfghjklzxcvbnm\"\',.;:?!"
const number_of_runes = 30
const runes: Rune[] = $state([])
const colors: string[] = ["purple", "red", "white", "black", "green", "turquoise", "yellow", "orange", "springgreen", "deeppink", "deepskyblue"]

function generateRunes(){
    for(let i = 0; i < number_of_runes; i++){
        runes.push({
            character: possibleRunes.charAt(Math.random() * possibleRunes.length),
            x: Math.random() * 120 - 20,
            size: Math.random(),
            color: colors[Math.round(Math.random() * colors.length)]
        })
    }
}

const animateRune: Action = (node) => {
    node.animate([{
        bottom: "-20%",
    }, {
        bottom: "120%",
    }], {
        duration: (Math.random() * 15000) + 5000,
        delay: Math.random() * 20,
        easing: "linear",
        iterations: Infinity,
        fill: "backwards"
    })
}

onMount(() => {
    generateRunes()
})

</script>

<div class="w-full h-full absolute pointer-events-none opacity-20">
    {#each runes as rune}
        <p 
            use:animateRune 
            style:color={rune.color} 
            style:left="{rune.x}%" 
            style:transform="scale(max({rune.size}, 0.3))" 
            style:filter="drop-shadow(0px 0px 10px {rune.color})"
            class="rune absolute"
        >
            {rune.character}
        </p>
    {/each}
</div>

<style> 
    .rune{
        font-family: "DARUNE";
        font-weight: 400;
        font-style: normal;
        font-size: 10em;
    }
</style>