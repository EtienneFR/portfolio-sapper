<script>
    import Page from '../components/Page.svelte';
    import Footer from '../components/Footer.svelte';

    const contact = [
        {
            href: 'https://github.com/EtienneFR/',
            src: 'github.svg',
            alt: 'github_icon',
        },
        {
            href: 'https://linkedin.com/in/etienne-dayre/',
            src: 'linkedin.svg',
            alt: 'linkedin',
        },
        {
            href: 'mailto:contact@etienne-dayre.fr',
            src: 'email.svg',
            alt: 'email_icon',
        },
    ];
</script>

<style>
    :global(.mode-dark) img[alt*='icon'] {
        -webkit-filter: invert(100%);
        filter: invert(100%);
    }
</style>

<svelte:head>
    <title>Etienne Dayre | Contact</title>
</svelte:head>

<Page>
    <div class="py-8 m-auto text-center lg:w-full">
        <h1 class="text-2xl text-blue-600">Contact</h1>
    </div>

    <div class="flex flex-col">
        {#each contact as { href, src, alt }}
            <div class="flex justify-center p-3">
                <a {href} target="_blank" rel="noopener">

                    <img {src} {alt} class="object-scale-down h-12" />

                </a>
            </div>
        {/each}
    </div>
    <Footer />
</Page>
