<script>
    import { onMount } from 'svelte';

    export let url = '';
    export let alt = 'image';
    export let imageWidth = '100%';
    export let imageHeight = '';
    export let placeholderWidth = '100%';
    export let placeholderHeight = '400px';

    let image;
    let loaded = false;

    onMount(() => {

        image.src = url;

        image.onload = () => {
            loaded = true;
            image.style.cssText = `width: ${imageWidth}; height: ${imageHeight}`;
        };

    });

</script>

<style>
    .placeholder {
        position: relative;
        background-color: #F9F9F9;
        overflow: hidden;
    }

    .shimmer {
        width: 100%;
        height: 100%;
        -webkit-animation: loading 1s linear infinite;
        animation: loading 1s linear infinite;
    }

    .shimmer:before {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        width: 50%;
        height: 100%;
        background: -webkit-gradient(linear, left top, right top, color-stop(20%, transparent), to(#E5E5E5));
        background: -o-linear-gradient(left, transparent 20%, #E5E5E5 100%);
        background: linear-gradient(90deg, transparent 20%, #E5E5E5 100%);
    }

    .shimmer:after {
        content: "";
        position: absolute;
        top: 0;
        right: 0;
        width: 50%;
        height: 100%;
        background: -webkit-gradient(linear, left top, right top, from(#E5E5E5), color-stop(20%, transparent));
        background: -o-linear-gradient(left, #E5E5E5 0%, transparent 20%);
        background: linear-gradient(90deg, #E5E5E5 0%, transparent 20%);
    }

    img {
        -webkit-animation: fadein 1s forwards;
        animation: fadein 1s forwards;
    }

    @-webkit-keyframes fadein {
        from {
            opacity: 0;
        }
        to {
            opacity: 1;
        }
    }

    @keyframes fadein {
        from {
            opacity: 0;
        }
        to {
            opacity: 1;
        }
    }

    @-webkit-keyframes loading {
        from {
            -webkit-transform: translateX(-100%);
            transform: translateX(-100%);
        }
        to {
            -webkit-transform: translateX(100%);
            transform: translateX(100%);
        }
    }

    @keyframes loading {
        from {
            -webkit-transform: translateX(-100%);
            transform: translateX(-100%);
        }
        to {
            -webkit-transform: translateX(100%);
            transform: translateX(100%);
        }
    }
</style>

<img src="" alt="{alt}" bind:this={image} style="display: none;" />

{#if !loaded}
    <slot>
        <div class="placeholder" style="width: {placeholderWidth}; height: {placeholderHeight};">
            <div class="shimmer"></div>
        </div>
    </slot>
{/if}