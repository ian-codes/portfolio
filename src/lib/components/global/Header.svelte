
<script>
    let openedSubmenu = "";

    let burgerOpen = false;

    import {NavigationData} from "$lib/navigation.js";

    function handleMenuClick(name) {
        openedSubmenu = name != openedSubmenu ? name : ""
        console.log(openedSubmenu)
    }
</script>


<header>
    <div class="bg"></div>
    <a href="/" title="home" class="logo-wrapper">
        <div class="logo"></div>
    </a>
    <button on:click={() => burgerOpen = !burgerOpen} on:keydown={() => burgerOpen = !burgerOpen} 
        class="burger">
        <span></span>
        <span></span>
        <span></span>
    </button>
    <nav class="{burgerOpen ? "open" : ""}">
        <ol>
            {#each Object.keys(NavigationData) as menuItem}

                {#if NavigationData[menuItem] == ""}

                    <li class="menuItem">
                        <a class="menuItemLink" href="{menuItem}">{menuItem}</a>
                    </li>

                {:else}

                    <li class="menuItem">
                        <a href="#" on:click={event => handleMenuClick(event.target.innerText)}
                            class="menuItemLink {openedSubmenu == menuItem ? "active" : ""}">
                            {menuItem}
                        </a>

                        <ol class="submenu {openedSubmenu != menuItem ? "closed" : ""}">
                            {#each NavigationData[menuItem] as submenuItem}
                                <li>
                                    <a class="submenuItemLink" href="{menuItem}/{submenuItem}">{submenuItem}</a>
                                </li>
                            {/each}
                        </ol>
                    </li>

                {/if}

            {/each}
        </ol>
    </nav>
</header>
<p>individuell, persönlich, engagiert</p>


<style>
    p {
        width: 1000px;
        color: white;
        text-align: left;
        letter-spacing: 4px;
        word-spacing: 1em;
        font-size: .9em;
        font-style: italic;
        opacity: .8;
        margin: 1em auto;
        padding: .5em;
        background: linear-gradient(90deg, transparent 5%, rgba(255, 255, 255, 0.13), transparent);
    }

    .closed {
        display: none !important;
    }

    .submenu {
        position: absolute;
        display: flex;
        flex-direction: column;
        align-items: start;
        background: white;
        top: 2rem;
        padding: 0;
        list-style: none;
        box-shadow: 0 6px 20px rgba(0, 0, 0, 0.432);
        border-radius: 1em;
        width: max-content;
        overflow: hidden;
        gap: 0;
    }

    header {
        height: 60px;
        position: relative;
        max-width: calc(1100px - 4em);
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0 2em;
        margin: 0 auto;
        background: white;
        border-radius: 1em;
    }

    header::after {
        box-shadow: 0 0 2px 1px rgba(255, 255, 255, 0.37), -1px -1px 10px inset rgba(143, 143, 143, 0.254), 0 5px 3px rgba(0, 0, 0, 0.466);
        content: '';
        position: absolute;
        inset: 0;
        pointer-events: none;
        border-radius: 1em;
    }

    .bg {
        pointer-events: none;
        background: linear-gradient(90deg, rgb(49, 145, 201), rgb(23, 156, 149));
        inset: 0;
        position: absolute;
        left: 25%;
        clip-path: polygon(10% 0, 100% 0, 100% 100%, 0 100%);
        z-index: 1;
        border-top-right-radius: 1em;
        border-bottom-right-radius: 1em;
    }

    nav {
        z-index: 1;
    }

    ol {
        display: flex;
        flex-direction: row;
        list-style: none;
        gap: .5em;
    }

    li {
        width: 100%;
    }

    .menuItem {
        position: relative;
    }

    .menuItemLink {
        text-decoration: none;
        letter-spacing: 1px;
        color: white;
        /* text-transform: uppercase; */
        padding: .5em 1em;
        border-radius: .5em;
        transition: all .2s ease;
    }

    .submenuItemLink {
        display: block;
        text-decoration: none;
        color: black;
        padding: 1em;
        transition: all .2s ease;
        width: 100%;
    }

    .submenuItemLink:hover {
        background: rgba(109, 109, 109, 0.233);
    }

    .menuItemLink:hover, .active {
        background: white;
        color: black;
    }

    .logo-wrapper {
        padding: 0;
        z-index: 3;
    }

    .logo {
        background: url('/logo.svg');
        background-size: contain;
        background-position: center;
        background-position-y: 8px;
        background-repeat: no-repeat;
        width: 150px;
        height: 40px;
        padding: .5em;
    }

    @media (max-width: 1200px) {
        nav {
            display: none;
            flex-direction: column;
            position: absolute;
            right: 0;
            top: 4rem;
            background: black;
            width: 100%;
        }

        .open {
            display: flex;
        }

        ol {
            flex-direction: column;
        }

        .burger {
            background: none;
            border: none;
            margin: 0;
            padding: 0;
            z-index: 1;
            width: 30px;
            height: 30px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: space-evenly;
            gap: 5px;
            cursor: pointer;
        }

        .burger span {
            background: white;
            height: 4px;
            width: 100%;
        }
    }
</style>