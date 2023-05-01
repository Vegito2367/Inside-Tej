<script>
  import { createEventDispatcher } from "svelte";
  const dispatcher= new createEventDispatcher(); 
  export let buttonshit;

  let selectedButton=buttonshit[0];

  let currentButton;

  

  $:console.log(selectedButton.buttonName)

  const handleClick = (e) => 
  {
    

    for (let index = 0; index < buttonshit.length; index++) 
    {
      const element = buttonshit[index];
      if (element.buttonName === e.target.innerText)
      {
        selectedButton=element
      }
    }
  }

</script>

<main>
  <div class="buttonHolder">
    {#each buttonshit as leButton}
      <!-- svelte-ignore a11y-click-events-have-key-events -->
      <div class="carouselButton" on:click={(e)=>{handleClick(e)}} class:selectedButt={leButton.blogName === selectedButton.blogName}>{leButton.buttonName}</div>
    {/each}
  </div>
    
</main>


<style>
  .carouselButton{
    color: blue;
    background-color: yellow;
  }

  .carouselButton:hover{
    cursor: pointer;
  }

  .buttonHolder{
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
  }


  .selectedButt{
    color:red;
  }
</style>