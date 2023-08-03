
<script>
    let openedSubmenu = "";

    let burgerOpen = false;


    function handleMenuClick(name) {
        openedSubmenu = name != openedSubmenu ? name : ""
        console.log(openedSubmenu)
    }

    function formatLink(menuLink) {
        let newLink = menuLink.replace(' ', '-').toLowerCase()
        console.log(newLink)
        return newLink
    }
</script>


<header>
    <button on:click={() => burgerOpen = !burgerOpen} on:keydown={() => burgerOpen = !burgerOpen} 
        class="burger">
        <span></span>
        <span></span>
        <span></span>
    </button>

    <div class="logoWrapper">
        <a id="logo" href="/" title="home">
            ian-codes
        </a>
    </div>

 
    <nav class="{burgerOpen ? "open" : ""}">
        <ol>
            <li class="menuItem">
                <a class="menuItemLink" href="#web-design">Web Design</a>
            </li>

            <li class="menuItem">
                <a class="menuItemLink" href="#digital-marketing">Digital Marketing</a>
            </li>

            <li class="menuItem">
                <a class="menuItemLink" href="#about">Über mich</a>
            </li>

            <li class="menuItem">
                <a class="menuItemLink" href="#kontakt">Kontakt</a>
            </li>
        </ol>
    </nav>
</header>


<style>
    #logo {
        color: white;
        text-decoration: none;
        letter-spacing: 3px;
        font-size: 2rem;
        padding: 4px 12px;
        border-radius: .5em;
    }

    #logo:hover {
        color: black;
        background: white;
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
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 3em 2em;
        margin: 0 auto;
        max-width: 1100px;
        width: 100%;
        margin-bottom: 4em;
    }

    nav {
        z-index: 1;
    }

    ol {
        display: flex;
        flex-direction: row;
        list-style: none;
        gap: 2em;
    }

    .menuItem {
        position: relative;
    }

    .menuItemLink {
        text-decoration: none;
        letter-spacing: 1px;
        color: white;
        padding: .5em 1em;
        border-radius: .5em;
        transition: all .2s ease;
    }

    #logo, .menuItemLink, .submenuItemLink {
        user-select: none;
    }

    .submenuItemLink {
        display: block;
        text-decoration: none;
        color: black;
        padding: 1em;
        transition: all .2s ease;
    }

    .submenuItemLink:hover {
        background: rgba(109, 109, 109, 0.233);
    }

    .menuItemLink:hover, .active {
        background: white;
        color: black;
    }

    .burger {
        display: none;
    }


    @media (max-width: 1200px) {
        header {
            justify-content: start;
            gap: 1em;
        }

        nav {
            display: none;
            flex-direction: column;
            position: absolute;
            right: 0;
            top: 6rem;
            width: 100%;
            border-radius: 1em;
            padding: 1em;
        }

        .logoWrapper {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 100%;
        }

        .open {
            display: flex;
        }

        ol {
            flex-direction: column;
            gap: 2em;
        }
        

        .burger {
            background: none;
            border: none;
            margin: 0;
            width: 38px;
            height: 34px;
            padding: 4px;
            z-index: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: space-between;
            cursor: pointer;
        }

        .burger span {
            background: white;
            height: 2px;
            width: 100%;
            margin: 3px 0;
        }
    }
</style>