<script>

import {onMount} from "svelte";
import {
  createEventDispatcher
} from "svelte";
import {
  element
} from "svelte/internal";
import {
  elasticOut,
  linear
} from "svelte/easing"
  import { fade, fly } from "svelte/transition";
const dispatcher = new createEventDispatcher();
export let buttonshit;

let selectedButton = buttonshit[0];
let vis=false



let underline

let buttonPos=[

]


function AssignPos(node){

  var rect=node.getBoundingClientRect()
  buttonPos.push({
    id:node.id,
    yposition:(rect.left + rect.right)/2
  })

}

  let left=0
  onMount(()=>{
    vis=true

    setTimeout(() => {
      left = 540;
    }, 0);
  })

  function moveUnderline(node, { xPosDes, duration }) {
  return {
    duration,
    css: (t) => {
      const ease = linear(t);

      const left = xPosDes * ease;
      

      // Calculate the final position
      const finalLeft = xPosDes;

      // Apply final styles progressively as the animation progresses
      const currentLeft = left + (finalLeft - left) * t;

      return `
        left: ${currentLeft}px;
        `
    },
  };
}
const handleClick = (e) => {
  for (let index = 0; index < buttonshit.length; index++) {
    const element = buttonshit[index];
    if (element.buttonName === e.target.innerText) {
      selectedButton = element
    }
  }

  console.log(buttonPos)

  
}

function getOffset(el) {
  const rect = el.getBoundingClientRect();
  return {
    left: rect.left + window.scrollX,
    top: rect.top + window.scrollY
  };
}



</script>

<main>
  {#if vis===true}
        <div class="sexyUnderline" id="coolUnderline" in:moveUnderline="{{xPosDes:540, duration:3000}}" bind:this={underline}
        ></div>
      {/if}
    <div class="buttonHolder" id="holder">
      
        {#each buttonshit as leButton}
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <div class="carouselButton" id={leButton.blogName} on:click={(e)=>{handleClick(e)}} class:selectedButt={leButton.blogName === selectedButton.blogName} use:AssignPos>
          {leButton.buttonName}
        </div>
        {/each}
    </div>

</main>

<style>
.carouselButton {
  color: blue;
  background-color: yellow;
}

.carouselButton:hover {
  cursor: pointer;
}

.buttonHolder {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  position: relative;
}

.selectedButt {
  color: red;
}

.sexyUnderline {
  position: absolute;
  width: 20px;
  height: 2px;
  background-color: black;
  z-index: 10000000;
  /* animation-name: moveTo;
  animation-duration: 0.5s;
  animation-fill-mode: forwards;
  animation-timing-function: linear; */
}

@keyframes moveTo {
  0% {
    left: 0px;
  }

  100%{
    left: 100px
  }

}
</style>
