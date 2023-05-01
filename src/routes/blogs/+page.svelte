<script>
  import Buttoncarousel from "../../lib/buttoncarousel.svelte";

  let inputData=[
    {buttonName:"Immigrant's Paradox", blogName:"ImmigParadox"},
    {buttonName:"Improvement Paradox", blogName:"ImprovParadox"},
    {buttonName:"Types of Friends", blogName:"FriendsBlog"},
    {buttonName:"Personal Thoughts", blogName:"PersonalThoughts"},
  ]
</script>

<main>
  <div class="Centerthisbadboy">
    So here are the buttons?
    <Buttoncarousel buttonshit={inputData} />
    
  </div>
  

</main>

<style>
  .Centerthisbadboy{
    text-align: center;
  }
</style>