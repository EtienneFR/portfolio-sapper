<script>
    import NavLink from './NavLink.svelte';
    import Theme from '../components/Theme.svelte';

    export let segment;

    const links = [
        {
            text: 'Accueil',
            link: '.',
            segment: undefined,
        },
        {
            text: 'À propos',
            link: 'about',
            segment: 'about',
        },
        {
            text: 'Compétences',
            link: 'skills',
            segment: 'skills',
        },
        {
            text: 'Projets',
            link: 'projects',
            segment: 'projects',
        },
        {
            text: 'Veilles',
            link: 'watchs',
            segment: 'watchs',
        },
    ];
    let isOpen;
    let classes;

    function buttonClick() {
        isOpen = !isOpen;
    }

    $: classes = `${
        isOpen ? 'flex' : 'hidden'
    } md:flex items-center flex-col md:flex-row md:justify-between`;

    function linkClick() {
        isOpen = false;
    }
</script>

<nav class="flex flex-wrap items-center justify-between px-3 py-3">
    <div class="flex items-center flex-shrink-0 mr-6" />
    <div class="block lg:hidden md:hidden">
        <button
            on:click={buttonClick}
            class="flex items-center"
            aria-label="Left Align">
            <span class="sr-only">Menu pour téléphone</span>
            <svg viewBox="0 0 20 20" fill="currentColor" class="w-10 h-10">
                <path
                    fill-rule="evenodd"
                    d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1
                    0 011-1h6a1 1 0 110 2H4a1 1 0 01-1-1zM3 15a1 1 0 011-1h12a1
                    1 0 110 2H4a1 1 0 01-1-1z"
                    clip-rule="evenodd" />
            </svg>
        </button>
    </div>
    <div class="flex flex-col justify-between w-full md:flex-row">
        <div on:click={linkClick}>
            <ul class={classes}>
                {#each links as { text, link, segment: linkSegment, alignEnd }, index}
                    <NavLink
                        addEndMargin={index !== links.length - 1}
                        {link}
                        isCurrentPage={segment === linkSegment}>
                        {text}
                    </NavLink>
                {/each}
            </ul>
        </div>
        <div on:click={linkClick}>
            <ul class={classes}>
                <NavLink link="contact" isCurrentPage={segment === 'contact'}>
                    Contact
                </NavLink>
            </ul>
        </div>
    </div>
    <div class="flex flex-row-reverse w-full pt-3">
        <div class="px-4 py-3">
            <Theme />
        </div>
    </div>
</nav>
