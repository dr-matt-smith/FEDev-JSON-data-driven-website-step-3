<!--<script>-->
<!--// export let params;  << $app/state is now the recommended method to access page parameters-->
<!--import { page } from '$app/state';-->
<!--let params = page.params;-->

<!--    let moduleCode = params.modulecode-->
<!--</script>-->

<!--<h1>-->
<!--    Details of module with code = {moduleCode}-->
<!--</h1>-->

<!--{#if moduleCode == "2027"}-->
<!--    <h3>COMP H2027 Front End Development</h3>-->
<!--    <p>-->
<!--        learn about Svelte and SvelteKit for dynamic website development-->
<!--    </p>-->
<!--{:else if moduleCode == "2029"}-->
<!--    <h3>COMP H2029 Database Fundamentals</h3>-->
<!--    <p>-->
<!--        learn database stuff-->
<!--    </p>-->
<!--{:else if moduleCode == "2031"}-->
<!--    <h3>H2031 Object-Oriented Programming</h3>-->
<!--    <p>-->
<!--        learn OO Java programming stuff-->
<!--    </p>-->
<!--{:else}-->
<!--    <p>ERROR - unknown module code</p>-->
<!--{/if}-->

<script>
    // export let params;  << $app/state is now the recommended method to access page parameters
    import { page } from '$app/state';
    let params = page.params;

    let moduleCode = params.modulecode;

    // default to unknown module code
    let moduleTitle = "ERROR";
    let moduleDetails = "unknown module code";

    if(moduleCode === "2027") {
        moduleTitle = "COMP H2027 Front End Development";
        moduleDetails = "learn about Svelte and SvelteKit for dynamic website development"
    }

    if(moduleCode === "2029") {
        moduleTitle = "COMP H2029 Database Fundamentals";
        moduleDetails = "learn database stuff"
    }

    if(moduleCode === "2031") {
        moduleTitle = "COMP H2031 Object-Oriented Programming";
        moduleDetails = "learn OO Java programming stuff"
    }

</script>

<h1>
    Details of module with code = {moduleCode}
</h1>

<h3>{moduleTitle}</h3>
<p>
    {moduleDetails}
</p>