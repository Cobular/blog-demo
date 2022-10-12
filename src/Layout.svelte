<script context="module">
  // Import and re-export the custom implementations of each component here!
  // Use this for styling each component, for fonts and shit
	import h1 from "./components/h1.svelte";
  export {h1};
</script>

<script>
  // Load the following from frontmatter. 
  // May not handle something not being provided very well, we should provide a default by saying 
  // export let thing = <default_value> 
  /** @type {string} */
  export let title;
  /** @type {string} */
  export let desc;
  /** @type {number} */
  export let updated;
  /** @type {number} */
  export let created;

  // Do some logic on these values to format them if we want! We'll use this to reinterpret the unix timestamp as a js date.
  const updated_date = new Date(updated)
</script>



<content>
  <div id="innercontent">
    <!-- Display whatever we want above, around, and whatnot -->
    <h1>{title}</h1>
    <p>Updated: {updated_date.toString()}</p>
    <p>{desc}</p>

    <!-- Need a <slot />, the content will be rendered here -->
    <slot />
  </div>
</content>

<style>
  /* Center the content and stuff, give it a max width */
  content {
    width: 100%;
    padding: 5px;
    display: flex;
    flex-direction: row;
    justify-content: center;
  }
  #innercontent {
    max-width: 90ch;
  }
</style>
