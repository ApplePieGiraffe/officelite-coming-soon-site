<script>
    export let type = 'blue';
    export let wide = false;
    export let shadow = false;
    export let link = false;
    export let href = '.';

    function createRipple(e) {
        let btn = e.target;
        let boundingBox = e.target.getBoundingClientRect();
        let x = e.clientX - boundingBox.left;
        let y = e.clientY - boundingBox.top;

        let circle = document.createElement('span');
        circle.style.left = `${x}px`;
        circle.style.top = `${y}px`;
        circle.classList.add('ripple');

        if (btn.classList.contains('blue')) {
            circle.style.backgroundColor = 'white';
        }

        btn.appendChild(circle);

        circle.addEventListener('animationend', () => { circle.remove() });
    }
</script>

{#if link}
    <button class={type} class:wide={wide} class:shadow={shadow} on:click={(e) => {createRipple(e)}} onclick="location.href='{href}'">
        <slot></slot>
    </button>
{:else}
    <button class={type} class:wide={wide} class:shadow={shadow} on:click={(e) => {createRipple(e)}}>
        <slot></slot>
    </button>
{/if}

<style>
    button {
        position: relative;
        width: 21.375rem;
        height: 7rem;
        border: none;
        border-radius: 100rem;
        font-size: 2rem;
        font-family: inherit;
        line-height: 3.5rem;
        cursor: pointer;
        transition: all .3s, outline 0s;
        overflow: hidden;
    }

    /* wide */

    .wide {
        width: 100%;
    }

    /* colors */

    .blue {
        background-color: #5175FF;
        color: white;
    }

    .blue:hover {
        background-color: #829CFF;
    }

    .light-blue {
        background-color: rgba(81, 117, 255, .15);
        color: #5175FF;
    }

    .light-blue:hover {
        background-color: rgba(81, 117, 255, .25);
    }

    .white {
        background-color: white;
        color: #5175FF;
    }

    .white:hover {
        background-color: white;
        color: #829CFF;
    }

    .white:focus {
        outline: 2px dotted white;
    }

    /* shadow */

    .shadow {
        box-shadow: 0px 25px 25px -10px rgba(63, 91, 194, 0.25);
    }

    button:active.shadow {
        box-shadow: 0px 15px 15px -10px rgba(63, 91, 194, 0.45);
    }

    /* ripple */

    :global(span.ripple) {
        position: absolute;
        transform: translate(-50%, -50%);
        width: 0;
        height: 0;
        border-radius: 50%;
        background-color: #5175FF;
        pointer-events: none;
        opacity: .25;
        animation: ripple .5s linear;
    }

    @keyframes ripple {
        to {
            width: 250px;
            height: 250px;
            opacity: 0;
        }
    }
</style>