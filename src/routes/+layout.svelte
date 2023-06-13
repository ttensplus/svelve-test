<nav>
    <div class="nav-container">
        <a href="/" class="nav-logo" title="Back to Homepage">Timo Klimov</a>
        <div class="nav-links">
            {#each nav as link}
                <a href={link.href} class="link">{link.title}</a>
            {/each}
        </div>
    </div>
</nav>
<div class="container">
    <slot></slot>
</div>


<script>
    const nav = [
        {
            title: 'About me',
            href: '/about'
        },
        {
            title: 'Blog',
            href: '/blog'
        },
        {
            title: 'Portfolio',
            href: '/project'
        },
        {
            title: 'Contacts',
            href: '/contact'
        },
        {
            title: 'temp',
            href: '/temp'
        },
    ]
</script>
<style>
    .container {
        max-width: 1400px;
        margin: 50px auto;
    }
</style>