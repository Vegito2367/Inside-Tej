<script>
import Link from "../lib/link.svelte";
</script>

<header></header>

<main>
    <div class="HeaderButtons">
        <Link destination="/" displayText="Home" />
        <Link destination="/about" displayText="About" />
        <Link destination="/projects" displayText="Projects" />
        <Link destination="/blogs" displayText="Blogs" />
    </div>

    <slot />
</main>

<footer></footer>

<style>
@import url('https://fonts.googleapis.com/css2?family=PT+Sans:wght@400;700&display=swap');

  .HeaderButtons{
    display: flex; 
    column-gap:5px;
    justify-content: center;
    margin-bottom: 30px;
  }
</style>
