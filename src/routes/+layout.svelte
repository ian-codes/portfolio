<script>
    import Header from "../lib/components/global/Header.svelte";
    import Footer from "../lib/components/global/Footer.svelte";

</script>

<Header />
<main>
    <slot>

    </slot>
</main>
<Footer />

<div class="bg"></div>
<div class="border"></div>

<style>
    .bg {
        background-image: url('mountain.jpg');
        background-size: cover;
        background-repeat: no-repeat;
        position: fixed;
        inset: 0;
        z-index: -2;
        pointer-events: none;
        filter: brightness(.5);
    }

    .border {
        position: fixed;
        inset: 0;
        border: 2px solid black;
        pointer-events: none;
        z-index: -1;
    }
</style>