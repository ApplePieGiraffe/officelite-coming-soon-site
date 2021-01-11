<script>
    // components
    import Button from '../shared/Button.svelte';

    // drop-down menu
    let activeMenu = false;

    function toggleMenu() {
        activeMenu = activeMenu === true ? false : true;
    }

    // plans
    let plans = [
        {
            name: 'Basic Pack',
            price: 'Free',
            selected: true,
            id: 0,
        },
        {
            name: 'Pro Pack',
            price: '$9.99',
            selected: false,
            id: 1,
        },
        {
            name: 'Ultimate Pack',
            price: '$19.99',
            selected: false,
            id: 2,
        },
    ];

    let selectedPlan = plans.filter((plan) => { return plan.selected === true })[0];
    $: selectedPlan = plans.filter((plan) => { return plan.selected === true })[0];

    function selectPlan(id) {
        plans.forEach((plan) => { 
            if (plan.id === id) {
                plan.selected = true;
            } else {
                plan.selected = false;
            }
        });
        plans = plans;
    }
</script>

<form on:submit|preventDefault>
    <div class="container">
        <input required id="name" type="text" placeholder="Name">
        <label for="name">Name</label>
    </div>

    <div class="container">
        <input required id="email" type="email" placeholder="Email">
        <label for="email">Email</label>
    </div>

    <div class="plan-container">
        <div class="plan" class:selected={activeMenu} on:click={toggleMenu}>
            <span class="plan__name">{selectedPlan.name}</span>
            <span class="plan__price">{selectedPlan.price}</span>
        </div>
    
        <ul class:active={activeMenu} on:click={toggleMenu}>
            {#each plans as plan (plan.id)}
                <li class:selected={plan.selected} on:click={() => {selectPlan(plan.id)}}>{plan.name} <span>{plan.price}</span></li>
            {/each}
        </ul>
    </div>

    <div class="container">
        <input required id="tel" type="tel" placeholder="Phone Number">
        <label for="tel">Phone Number</label>
    </div>

    <div class="container">
        <input required id="company" type="text" placeholder="Company">
        <label for="company">Company</label>
    </div>

    <Button wide=true>Get on the list</Button>
</form>

<style>
    form {
        display: flex;
        flex-direction: column;
        width: 100%;
        max-width: 55.625rem;
        border-radius: 13px;
        box-shadow: 0px 50px 50px -25px rgba(75, 92, 154, 0.247159);
        padding: 4rem 5.25rem;
        padding-bottom: 6.5rem;
        background-color: white;
    }

    /* inputs */

    .container {
        position: relative;
        width: 100%;
        margin-bottom: 3rem;
        border-bottom: 1px solid rgba(116,123,149,.5);
        transition: .5s;
    }

    /* .container.invalid {
        border-bottom: 1px solid var(--color-red);
    } */

    .container::after {
        content: url(/img/sign-up/icon-cross.svg);
        position: absolute;
        top: 1rem;
        right: 3.5rem;
        transform: rotate(180deg);
        opacity: 0;
        transition: .5s;
    }

    /* .container.invalid::after {
        transform: rotate(0);
        opacity: 1;
    } */

    input, 
    .plan {
        position: relative;
        width: 100%;
        height: 5.625rem;
        border: none;
        color: #333950;
        font-size: 2rem;
        line-height: 3.5rem;
    }

    /* .container.invalid input {
        color: var(--color-red);
    } */

    input:focus {
        outline: none;
    }

    input::placeholder {
        color: transparent;
    }

    label {
        position: absolute;
        left: 0;
        transform: translateY(-1.5rem);
        color: rgba(116, 123, 149, .5);
        font-size: 1.5rem;
        line-height: 3.5rem;
        transition: .3s;
    }

    input:placeholder-shown + label {
        font-size: 2rem;
        transform: translate(0);
    }

    input:focus + label {
        font-size: 1.5rem;
        transform: translateY(-1.5rem);
    }

    /* plan */

    .plan-container {
        position: relative;
    }

    .plan {
        /* position: relative; */
        margin-bottom: 3rem;
        border-bottom: 1px solid rgba(116,123,149,.5);
        cursor: pointer;
    }

    .plan::after {
        content: url(/img/sign-up/icon-arrow-down.svg);
        position: absolute;
        right: 3.5rem;
        transform: rotate(180deg);
        opacity: 0;
        transition: .5s;
    }

    .plan:hover::after {
        opacity: 1;
    }

    .plan.selected::after {
        transform: rotate(0);
        opacity: 1;
    }

    .plan__name {
        color: #333950;
        font-size: 2rem;
        font-weight: 700;
        line-height: 3.5rem;
    }

    .plan__price {
        position: relative;
        display: inline-block;
        margin-left: 1rem;
        color: rgba(51, 57, 80, .4);
        transition: .3s;
    }

    .plan__price::before {
        content: '';
        position: absolute;
        top: 12px;
        left: -12px;
        width: 5px;
        height: 2px;
        background-color: transparent;
        transition: .3s;
    }

    .plan:hover .plan__price {
        margin-left: 2rem;
    }

    .plan:hover .plan__price::before {
        background-color: #333950;
    }

    /* drop-down menu */

    ul {
        position: absolute;
        top: 7rem;
        z-index: 10;
        width: 100%;
        max-width: 45.825rem;
        border: 1px solid rgba(51, 57, 80, 0.153273);
        border-radius: 8px;
        box-shadow: 0px 50px 50px -25px rgba(75, 92, 154, 0.747077);
        padding: 1rem 4rem;
        background-color: white;
        list-style: none;

        visibility: hidden;
        opacity: 0;
        transition: visibility 0s, opacity .3s;
    }

    li {
        position: relative;
        padding: 2rem 0;
        color: #333950;
        font-size: 2rem;
        font-weight: 700;
        line-height: 3.5rem;
        cursor: pointer;
    }

    li:not(:last-child) {
        border-bottom: 1px solid rgba(116, 123, 149, .25);
    }

    li.selected::after {
        content: url(/img/sign-up/icon-check.svg);
        position: absolute;
        right: 0;
    }

    li span {
        position: relative;
        display: inline-block;
        margin-left: 1rem;
        color: rgba(51, 57, 80, .4);
        transition: .3s;
    }

    li:hover span {
        margin-left: 2rem;
    }

    span::before {
        content: '';
        position: absolute;
        top: 12px;
        left: -12px;
        width: 5px;
        height: 2px;
        background-color: transparent;
        transition: .3s;
    }

    li:hover span::before {
        background-color: #333950;
    }

    /* drop-down menu | inactive */

    ul.active {
        visibility: visible;
        opacity: 1;
    }
</style>