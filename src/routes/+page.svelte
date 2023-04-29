<script>
  import Link from "./link.svelte";
</script>

<main>
  Hi its tej, Welcome to my website
  <div style="display: flex; column-gap:5px;">
    <Link destination="/about" displayText="About" />
    <Link destination="/projects" displayText="Projects" />
    <Link destination="/blogs" displayText="Blogs" />
  </div>
  
</main>




<style>
  :global(body) {
  background-color: #DDFFBB;
}
</style>