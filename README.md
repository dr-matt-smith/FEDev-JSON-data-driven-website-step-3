JSON-driven website: 
[Step 1](https://github.com/dr-matt-smith/FEDev-JSON-data-driven-website-step-1)
|
[Step 2](https://github.com/dr-matt-smith/FEDev-JSON-data-driven-website-step-2)
|
[Step 3](https://github.com/dr-matt-smith/FEDev-JSON-data-driven-website-step-3)


# FEDev-JSON-data-driven-website-step-3

Step-by-step development of a module details website. Routing in the form `/module/2037`


## 1: Use "IF" statement to customise the module details page

![custom module content](/screenshots/4_customer_content.png)

Since we only have 3 modules to deal with, let's hard-code responses to each of the 3 module codes.

NOTE: This would be a very poor approach for any larger number of modules!

We make use of the IF -ELSE IF - ELSE blocks of the Svelte framework
- note the different characters for the beginning `#`, middle `:` and end `/` of the conditional blocks
```html
{#if <condition1>}
    content for condition 2
{:else if <condition2>}
    content for condition 2
{:else}
    default content
{/if}
```

Update script `/routes/modules/[modulecode]/+page.svelte` to the following:
```html
<script>
    export let params;
    let moduleCode = params.modulecode
</script>

<h1>
    Details of module with code = {moduleCode}
</h1>

{#if moduleCode == "2027"}
    <h3>COMP H2027 Front End Development</h3>
    <p>
        learn about Svelte and SvelteKit for dynamic website development
    </p>
{:else if moduleCode == "2029"}
    <h3>COMP H2029 Database Fundamentals</h3>
    <p>
        learn database stuff
    </p>
{:else if moduleCode == "2031"}
    <h3>H2031 Object-Oriented Programming</h3>
    <p>
        learn OO Java programming stuff
    </p>
{:else}
    <p>ERROR - unknown module code</p>
{/if}
```


## 2: Move logic into the JavaScript section of the Svelte page

Rather than doing the logic in the HTML content section, let's move the logic into the JavaScript part of our script, so that our HTML content is as simple as outputting the contents of JavaScript variables `moduleTitle` and `moduleDetails`.

This approach is good preparation for when the title and details come from a JSON data source, rather than being hard coded.

Again, we are trying to ensure that the main job of our Svelte page is to decorate data with HTML and CSS
- we'll move the decision logic out of this page in a later step....

Update script `/routes/modules/[modulecode]/+page.svelte` to the following:
```html
<script>
    export let params;
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
```
