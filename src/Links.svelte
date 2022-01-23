<script lang="ts" context="module">
    export interface Link {
        href: string;
        text: string;
    }
</script>


<script lang="ts">
    export let links: Link[];
</script>


<ul>
    {#each links as link}
        <a href={link.href}>
            <li>{link.text}</li>
        </a>
    {/each}
</ul>


<style>
    ul {
        list-style: none;

        width: 100%;
        margin: 0;
        padding: 0;

        display: flex;
        flex-direction: column;
    }

    li {
        width: 100%;


        font-family: "Analogue Italic";
        font-size: 1.5rem;
    }

    a {
        text-decoration: inherit;
        color: inherit;
        
        padding: 1rem;
        margin-top: 1rem;
        text-align: center;
        border: 2px solid black;
    }

    a:first-child {
        margin-top: 0;
    }
</style>