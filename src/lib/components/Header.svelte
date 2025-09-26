<script lang="ts">
    import { onMount } from "svelte";
    import { page } from "$app/stores";
    import { get } from "svelte/store";

    import Breadcrumbs from '$components/Breadcrumbs.svelte'
    let header: HTMLElement;

    function isActive(href: string): boolean {
        const path = get(page).url.pathname;

        const normalize = (s: string) => {
            const n = s.replace(/\/+$/, "");
            return n === "" ? "/" : n;
        };

        const current = normalize(path);
        const target = normalize(href);

        if (target === "/") return current === "/";

        //active if exact match OR inside a subtree, like /tjanster
        return current === target || current.startsWith(target + "/");
    }

    const hasBreadcrumbs = isActive('/tjanster') || isActive('/case')

    onMount(() => {
        let prevScrollpos = 0;

        function handleHeaderScroll() {
            const currentScrollPos = window.scrollY;

            if (prevScrollpos <= currentScrollPos ){
                header.classList.add("scrolled");
            } else {
                header.classList.remove('scrolled');
            }

            prevScrollpos = currentScrollPos;
        }

        window.addEventListener('scroll', handleHeaderScroll)
    })
</script>

<header bind:this={header} class:has-breadcrumbs={hasBreadcrumbs}>
    <div class="header-container">
        <div class="logo-container">
            <img src="/images/cw_logo.svg" alt="createweb logotyp"/>
        </div>
        <nav>
            <ul>
                <li>
                    <a href="/" class:active={isActive("/")} class="link-navigation">Hem</a>
                </li>
                <li>
                    <a href="/case" class:active={isActive("/case")} class="link-navigation">Case</a>
                </li>
                <li>
                    <div class:active={isActive("/tjanster")} class="link-navigation dropdown">Tjänster</div>
                </li>
                <li>
                    <a href="/om-oss" class:active={isActive("/om-oss")} class="link-navigation">Om oss</a>
                </li>
                <li>
                    <a href="/kontakt" class:active={isActive("/kontakt")} class="link-navigation">Kontakt</a>
                </li>
            </ul>
        </nav>
        <div class="button-container">
            <a class="cw-button--primary small" href="">Begär en offert</a>
        </div>
        <div class="hamburger-container">
            <div class="subheading text-accent">meny</div>
        </div>
    </div>
    <div class="breadcrumbs-container">
        <Breadcrumbs></Breadcrumbs>
    </div>
</header>