<script>
    // components
    import Countdown from '../shared/Countdown.svelte';
    import Button from '../shared/Button.svelte';
</script>

<footer>
    <div class="bg"></div>
    <Countdown/>
    <Button link=true href='signup'>Get Started</Button>
</footer>

<style>
    footer {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-between;
        padding: 12.5rem 0;
    }

    .bg {
        position: absolute;
        left: 0;
        bottom: 0;
        z-index: -1;
        width: 100%;
        height: 160.5rem;
        background-image: url(/img/home/bg-pattern-footer.svg);
        background-position: 50% 250%;
        background-repeat: no-repeat;
        background-size: 150.25rem;
        background-color: var(--color-very-dark-grey);
    }

    /* media queries */

    @media only screen and (min-width: 750px) {
        .bg {
            height: 123.25rem; 
            background-position: 50% 5%;
            background-size: 181.75rem;
        }
    }

    @media only screen and (min-width: 1200px) {
        footer {
            flex-direction: row;
            align-items: center;
            justify-content: space-between;
            padding-top: 10.25rem;
            padding-bottom: 11.375rem;
        }

        .bg {
            height: 75.375rem;
            background-position: right 106px top -614px;
            background-size: 254.5rem;
        }
    }
</style>