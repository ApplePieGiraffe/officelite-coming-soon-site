<script>
    // components
    import Button from './Button.svelte';
    // props
    export let plan;
    export let price;
    export let description;
    export let feature1;
    export let feature2;
    export let feature3;
    export let blue = false;
</script>

<article class:blue={blue}>
    <h3>{plan}</h3>
    <p class="price">{price}</p>
    <p class="description">{description}</p>
    <ul>
        <li>{feature1}</li>
        <li>{feature2}</li>
        <li>{feature3}</li>
    </ul>
    {#if blue}
        <Button type='white' link=true href='signup'>Try for Free</Button>
    {:else}
        <Button type='light-blue' link=true href='signup'>Try for Free</Button>
    {/if}
</article>

<style>
    article {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 100%;
        max-width: 41.25rem;
        margin: 0 auto;
        border-radius: 13px;
        box-shadow: 0px 50px 50px -25px rgba(75, 92, 154, 0.247159);
        padding: 5rem 0;
        background-color: white;
        text-align: center;
    }

    h3, p {
        color: var(--color-dark-grey);
    }

    h3 {
        margin-bottom: 5rem;
        font-size: 2.5rem;
        line-height: 3.5rem;
    }

    .price {
        margin-bottom: 1rem;
        font-size: 7rem;
        font-weight: 700;
        line-height: 8rem;
    }

    .description, ul {
        font-size: 2rem;
        line-height: 3.5rem;
    }

    .description {
        margin-bottom: 7rem;
    }

    ul {
        margin-bottom: 4rem;
        list-style: none;
        color: var(--color-grey);
    }

    li:not(:last-child) {
        margin-bottom: 2rem;
    }

    /* blue */

    .blue {
        background-image: url(/img/home/bg-pattern-pricing.svg);
        background-size: 110rem;
        background-position: 50% 102%;
        background-repeat: no-repeat;
        background-color: var(--color-blue);
    }

    .blue h3,
    .blue .price,
    .blue .description,
    .blue ul {
        color: white;
    }

    .blue ul {
        opacity: .75;
    }

    /* media queries */

    @media only screen and (min-width: 750px) {
        article {
            flex-wrap: wrap;
            align-items: flex-start;
            max-width: 86.125rem;
            height: 39.5rem;
            padding: 6rem;
            text-align: start;
        }

        ul {
            order: 1;
            margin-top: 5.5rem;
        }

        h3 {
            margin-bottom: 2rem;
        }

        .price {
            margin-bottom: .5rem;
        }

        .description {
            margin-bottom: 3rem;
        }

        .blue {
            background-position: 200% 50%;
        }
    }

    @media only screen and (min-width: 1200px) {
        article {
            flex-wrap: nowrap;
            align-items: center;
            max-width: initial;
            height: initial;
            padding: 5rem 0;
            text-align: center;
        }

        ul {
            order: 0;
            margin-top: 0;
        }

        h3 {
            margin-bottom: 5rem;
        }

        .price {
            margin-bottom: 1rem;
        }

        .description {
            margin-bottom: 7rem;
        }

        .blue {
            background-position: 50% 102%;
        }
    }
</style>