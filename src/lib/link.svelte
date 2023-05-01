<script>


  export let destination="/";
  export let displayText="Next Webpage";
</script>


<main>
  <a href={destination} style="text-decoration: none;">
    <div class="button" >{displayText}</div>
    
  </a>
</main>

<style>
  @import url('https://fonts.googleapis.com/css2?family=PT+Sans:wght@400;700&display=swap');

  .button{
    background-color: orangered;
    color: white;
    display: inline-block;
    font-size: 25px;
    border-radius: 10px;
    padding: 3px 15px 3px 15px;
    font-family: 'PT Sans';
  }
</style>