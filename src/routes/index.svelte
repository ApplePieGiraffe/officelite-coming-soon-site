<script>
    // components
    import Header from '../components/home/Header.svelte';
    import Hero from '../components/home/Hero.svelte';
    import Plans from '../components/home/Plans.svelte';
    import Footer from '../components/home/Footer.svelte';
    import Attribution from '../components/shared/Attribution.svelte';
</script>

<svelte:head>
	<title>Frontend Mentor | Officelite Coming Soon Site</title>
</svelte:head>

<div class="container">
    <Header/>
    <Hero/>
    <Plans/>
    <Footer/>
    <Attribution/>
</div>

<style>
    :global(body) {
        padding: 0 3rem;
        padding-top: 5.75rem;
        background-image: url(/img/home/bg-pattern-header.svg);
        background-color: var(--color-very-light-grey);
        background-position: 50% -50%;
        background-repeat: no-repeat;
        background-size: 120vw;
    }

    .container {
        max-width: 1110px;
        margin: 0 auto;
    }

    @media only screen and (min-width: 600px) {
        :global(body) {
            padding: 0 5rem;
            padding-top: 10.125rem;
            background-position: 45.55vw -52.375rem;
            background-size: 141.75rem;
        }
    } 
</style>