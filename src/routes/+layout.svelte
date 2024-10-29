<script lang="ts">
    import "../app.css"
    interface Props {
        children?: import('svelte').Snippet;
    }

    let { children }: Props = $props();
</script>

<svg width="0" height="0">
    <defs>
        <clipPath id="clipBezier" clipPathUnits="objectBoundingBox">
            <path d="M 0.02,0.026 q 0.48,-0.0335 0.96,0 q 0.03,0.48 0,0.96 q -0.48,0.0335 -0.96,0 q -0.03,-0.48 0,-0.96 Z" />
        </clipPath>
    </defs>
</svg>


<section class="flex justify-center items-center h-full w-full">
    <div id="mold" class="flex justify-center items-center relative shadow-lg">
        <div id="bevel" class="flex justify-center items-center relative">
            <div id="screen"></div>
            <main class="absolute text-[#dddd]">
                {@render children?.()}
            </main>
        </div>
    </div>
</section>


<style>
    main {
        aspect-ratio: 4/3;
        height: 95%; 
        filter: blur(1px);
        overflow: hidden;
    }

    section{
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        background: radial-gradient(circle at 50% 50%, rgb(56, 56, 56), black);
    }

    #screen{
        height: 95%;
        aspect-ratio: 4/3;
        background: linear-gradient(
            rgba(95, 95, 95, 0.1),
            rgba(95, 95, 95, 0.1) 3px,
            transparent 3px,
            transparent 5px
        );
        background-size: 100% 5px;
        animation: pan-overlay 22s infinite linear;
        z-index: 100;
        overflow: hidden;
        box-shadow: inset 0 0 30px 25px rgba(39, 39, 39, 0.25);
        pointer-events: none;
    }

    #mold{
        height: 90%;
        aspect-ratio: 4/3;
        border-radius: 5px;
        border: .25rem solid;
        background: radial-gradient( circle at 0% 0%,
            rgb(34, 34, 34) 40%,
            rgb(24, 24, 24) 60%,
            rgb(14, 14, 14) 100%
        );
        border-top-color: rgb(44, 44, 44);
        border-right-color: rgb(18, 18, 18);
        border-bottom-color: rgb(18, 18, 18);
        border-left-color: rgb(56, 56, 56);
    }

    #bevel{
        height: 90%;
        aspect-ratio: 4/3;
        border-radius: 5px;
        background: linear-gradient( to right, rgba(18, 18, 18, .5 ) 0%, rgba(34, 34, 34, .5 ) 100% ),
        linear-gradient( to bottom, rgba(18, 18, 18, .75 ) 0, rgba(34, 34, 34, .5 ) 100% );
    }

    @keyframes pan-overlay {
        from {
            background-position: 0% 0%;
        }
        to {
            background-position: 0% -100%;
        }
    }
</style>