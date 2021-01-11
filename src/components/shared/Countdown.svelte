<script>
    export let alt = false;

    let date = new Date();
    date.setDate(date.getDate() + 47);
    date.setHours(date.getHours() + 7);
    date.setMinutes(date.getMinutes() + 56);
    date.setSeconds(date.getSeconds() + 14);

    let seconds;
    let minutes;
    let hours;
    let days;

    function countdown() {
        let timeLeft = date - new Date();

        seconds = Math.floor((timeLeft / 1000) % 60);
        minutes = Math.floor((timeLeft / 1000 / 60) % 60);
        hours = Math.floor((timeLeft / (1000 * 60 * 60)) % 24);
        days = Math.floor(timeLeft / (1000 * 60 * 60 * 24));
    }

    countdown();
    setInterval(countdown, 1000);
</script>

<div class="container" class:alt={alt}>
    <p>Coming <span>{`${date.getDate()} ${date.toLocaleString('default', { month: 'short' })} ${date.getFullYear()}`}</span></p>
    <div class="time-wrapper">
        <div class="cell">
            <span class="number">{days}</span>
            <span class="label">days</span>
        </div>

        <div class="cell">
            <span class="number">{hours.toString().padStart(2, '0')}</span>
            <span class="label">hours</span>
        </div>

        <div class="cell">
            <span class="number">{minutes}</span>
            <span class="label">min</span>
        </div>

        <div class="cell">
            <span class="number">{seconds}</span>
            <span class="label">sec</span>
        </div>
    </div>
</div>

<style>
    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
    }

    p,
    .number, 
    .label {
        color: white;
        font-weight: 700;
    }

    .alt p {
        color: var(--color-very-dark-grey);
    }

    .alt .number {
        color: var(--color-blue);
    }

    .alt .label {
        color: var(--color-grey);
    }

    p {
        margin-bottom: 2.25rem;
        font-size: 2rem;
        letter-spacing: 5px;
        line-height: 6rem;
        text-transform: uppercase;
    }

    p span {
        color: var(--color-blue);
    }

    .time-wrapper {
        display: flex;
        margin-bottom: 5rem;
    }

    /* time cells */

    .cell {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 9rem;
        border-radius: 4px;
        padding-top: 1.25rem;
        background-color: var(--color-dark-grey);
    }

    .alt .cell {
        background-color:rgba(233, 237, 251);
    }

    .cell:not(:last-child) {
        margin-right: 1.625rem;
    }

    .number {
        font-size: 4rem;
        line-height: 6rem;
    }

    .label {
        margin-bottom: 1.25rem;
        font-size: 1.5rem;
        line-height: 3.5rem;
        opacity: .5;
    }

    /* media queries */

    @media only screen and (min-width: 750px) {
        .cell {
            width: 12.5rem;
            border-radius: 13px;
            padding-top: 3rem;
        }

        .number {
            margin-bottom: 5.28px;
            font-size: 7rem;
        }

        .label {
            margin-bottom: 13.88px;
            font-size: 2rem;
        }
    }

    @media only screen and (min-width: 1200px) {
        .container {
            align-items: flex-start;
            text-align: start;
        }

        .time-wrapper {
            margin-bottom: 0;
        }

        p {
            margin-bottom: 0;
        }

        .cell {
            padding-top: 4rem;
        }

        .cell:not(:last-child) {
            margin-right: 2rem;
        }
    }
</style>