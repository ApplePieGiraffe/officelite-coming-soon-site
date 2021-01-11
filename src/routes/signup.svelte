<script>
    // components
    import Header from '../components/home/Header.svelte';
    import Countdown from '../components/shared/Countdown.svelte';
    import Form from '../components/signup/Form.svelte';
</script>

<svelte:head>
	<title>Frontend Mentor | Officelite Coming Soon Site</title>
</svelte:head>

<div class="container">
    <div class="bg"></div>
    <Header/>
    <div class="container-body">
        <div class="wrapper">
            <h1 class="heading heading--primary">Work smarter. Save time.</h1>
            <p class="body-copy body-copy-1">Easily manage your projects. Get on the list and receive in-app perks available only to early subscribers. We are moving into final development and getting ready for official launch soon.</p>
            <Countdown alt={true}/>
        </div>
        <Form/>
    </div>
</div>

<style>
    :global(body) {
        min-height: 100vh;
        padding: 0 3rem;
        padding-top: 5.75rem;
        background-image: url(/img/home/bg-pattern-header.svg);
        background-color: var(--color-very-light-grey);
        background-position: 50% -45vw;
        background-repeat: no-repeat;
        background-size: 120vw;
    }

    .bg {
        position: absolute;
        bottom: 0;
        left: 0;
        z-index: -1;
        width: 100%;
        height: 40rem;
        background-image: url(/img/home/bg-pattern-footer.svg);
        background-position: 50% 50%;
        background-repeat: no-repeat;
        background-size: 150rem;
        background-color: var(--color-very-dark-grey);
    }

    .container {
        max-width: 1110px;
        margin: 0 auto;
    }

    .container-body {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding-bottom: 11rem;
    }

    .wrapper {
        padding-top: 10rem;
        margin-bottom: 3rem;
    }

    h1, p {
        text-align: center;
    }

    h1 {
        margin-bottom: 2rem;
    }

    p {
        max-width: 71.5rem;
        margin: 0 auto;
        margin-bottom: 8rem;
    }

    @media only screen and (min-width: 600px) {
        :global(body) {
            padding: 0 5rem;
            padding-top: 10.125rem;
            background-image: initial;
        }

        .bg {
            height: 47.5rem;
            background-position: 50% 50%;
            background-size: 180rem;
        }

        p {
            margin: 0 auto;
            margin-bottom: 5rem;
        }
    }

    @media only screen and (min-width: 1200px) {
        .bg {
            top: 0;
            right: 0;
            left: initial;
            width: 30vw;
            height: 100%;
            background-position: 50% 90%;
            background-size: 254rem;
        }

        .container-body {
            flex-direction: row;
            align-items: flex-start;
            justify-content: space-between;
            padding-bottom: 20rem;
            padding-top: 15.75rem;
        }

        .wrapper {
            padding-top: 3rem;
        }

        h1, p {
            max-width: 67.5rem;
            text-align: start;
            margin: 0;
        }

        h1 {
            margin-bottom: 3rem;
        }

        p {
            margin-bottom: 5rem;
        }
    }
</style>