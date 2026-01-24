<script lang="ts">
    import { onMount } from "svelte";
    import logo from "$lib/assets/images/TEDlogo.jpg";

    let scrolled = false;

    onMount(() => {
        const handleScroll = () => {
            scrolled = window.scrollY > 50;
        };

        window.addEventListener("scroll", handleScroll);

        return () => {
            window.removeEventListener("scroll", handleScroll);
        };
    });

    function scrollToSection(sectionId: string, event: Event) {
        event.preventDefault();
        const element = document.getElementById(sectionId);
        if (element) {
            element.scrollIntoView({ behavior: "smooth" });
        }
    }
</script>

<header class:scrolled>
    <nav>
        <a
            href="#home"
            class="logo"
            on:click={(e) => scrollToSection("home", e)}
            ><img src={logo} alt="TED Logo" /></a
        >
        <ul class="nav-menu">
            <li>
                <a href="#about" on:click={(e) => scrollToSection("about", e)}
                    >학원소개</a
                >
            </li>
            <li>
                <a
                    href="#programs"
                    on:click={(e) => scrollToSection("programs", e)}>교육과정</a
                >
            </li>
            <li>
                <a
                    href="#admissions"
                    on:click={(e) => scrollToSection("admissions", e)}
                    >입학안내</a
                >
            </li>
            <li>
                <a
                    href="#contact"
                    on:click={(e) => scrollToSection("contact", e)}>오시는길</a
                >
            </li>
        </ul>
    </nav>
</header>

<style>
    header {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        z-index: 1000;
        background: rgba(255, 255, 255, 0.95);
        backdrop-filter: blur(10px);
        box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        transition: all 0.3s;
    }

    header.scrolled {
        box-shadow: 0 2px 20px rgba(0, 0, 0, 0.15);
    }

    nav {
        max-width: 1400px;
        margin: 0 auto;
        padding: 20px 40px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .logo {
        font-size: 24px;
        font-weight: 700;
        color: #2c3e50;
        text-decoration: none;
        transition: color 0.3s;
        display: flex;
        align-items: center;
        gap: 10px;
    }

    .logo img {
        height: 40px;
        width: auto;
    }

    .logo:hover {
        color: #3498db;
    }

    .nav-menu {
        display: flex;
        gap: 40px;
        list-style: none;
    }

    .nav-menu a {
        text-decoration: none;
        color: #2c3e50;
        font-weight: 500;
        transition: color 0.3s;
    }

    .nav-menu a:hover {
        color: #3498db;
    }

    @media (max-width: 768px) {
        .nav-menu {
            display: none;
        }
    }
</style>
