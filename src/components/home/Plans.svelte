<script>
    // components
    import Card from '../shared/Card.svelte';

    // data
    let plan1 = {
        plan: 'Basic',
        price: 'Free',
        description: 'Up to 5 users for free',
        feature1: 'Basic document collaboration',
        feature2: '2 GB storage',
        feature3: 'Great security and support',
        blue: false
    }

    let plan2 = {
        plan: 'Pro',
        price: '$9.99',
        description: 'Per user, billed monthly',
        feature1: 'All essential integrations',
        feature2: '50 GB storage',
        feature3: 'More control and insights',
        blue: true
    }

    let plan3 = {
        plan: 'Ultimate',
        price: '$19.99',
        description: 'Per user, billed monthly',
        feature1: 'Robust work management',
        feature2: '100 GB storage',
        feature3: 'VIP support',
        blue: false
    }
</script>

<section>
    <h2 class="sr-only">Plans</h2>
    <div class="card-container">
        <Card {...plan1}/>
        <Card {...plan2}/>
        <Card {...plan3}/>
    </div>
</section>

<style>
    section {
        padding-top: 12.5rem;
    }

    .card-container {
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: repeat(3, auto);     
        justify-content: center;
        grid-row-gap: 4rem;
    }

    @media only screen and (min-width: 1200px) {
        section {
            padding-top: 13.625rem;
        }

        .card-container {
            grid-template-columns: repeat(3, 1fr);
            grid-template-rows: auto;     
            grid-column-gap: 3.75rem;
        }
    }
</style>