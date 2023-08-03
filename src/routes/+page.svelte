<script>
    import WebDev from "$lib/components/WebDev.svelte";
    import DigitalMarketing from "$lib/components/DigitalMarketing.svelte";
    import About from "$lib/components/About.svelte";
    import Contact from "../lib/components/Contact.svelte";
</script>


<section>
    <h1>
        <a href="#web-design">
            Web Design & <wbr>-Development
        </a>

        <a href="https://kilendra.ch" target="_blank" title="kilendra.ch">
            <span>Digital Marketing</span>
            <div class="linkImg"></div>
        </a>
    </h1>
</section>

<WebDev />

<DigitalMarketing />

<About />

<Contact />

<style>
    section {
        height: 80vh;
        margin-top: 5em;
    }

    h1 {
        text-transform: uppercase;
        height: 100%;
        font-size: 3em;
        letter-spacing: 2px;
        color: white;
        text-align: center;
        display: flex;
        flex-direction: column;
        gap: 2em;
        word-break: normal;
    }

    a {
        text-decoration: none;
        color: white;
        user-select: none;
        padding: 1em 2em;
        background: linear-gradient(90deg, rgb(120, 186, 212), rgba(39, 130, 173, 0.63)) ;
        box-shadow: 0 10px 20px rgba(0, 0, 0, 0.144), -2px -2px 2px 4px rgba(255, 255, 255, 0.5), 2px 2px 2px 4px rgba(0, 0, 0, 0.514);
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: start;
        gap: 1em;
    }

    a:hover {
        background: linear-gradient(90deg, white, rgba(233, 233, 233, 0.616));
        color: black;
        transform: scale(1.02);
    }

    a:hover .linkImg {
        filter: invert(0);
    }

    .linkImg {
        background: url('/link.png');
        background-size: contain;
        background-position: center;
        background-repeat: no-repeat;
        min-width: 1em;
        min-height: 1em;
        width: 1em;
        height: 1em;
        filter: invert(1);
    }

    @media (max-width: 1080px) {
        h1 {
            font-size: 2em;
        }
    }

    @media (max-width: 400px) {
        h1 {
            font-size: 1rem;
            text-align: start;
        }
    }
</style>