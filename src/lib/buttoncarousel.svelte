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


let bodyRect
let xPosition
let yPosition


  onMount(()=>{
    vis=true
  })

function moveUnderline(node, {
    xPosDes,
    yPosDes,
    duration
  }) {
    return {
      duration,
      css: t => {
        const ease = linear(t) * 0.5

        return `
          left:${xPosDes*ease}px;
          top:${yPosDes*ease}px;
        `
      }
    }

  }

const handleClick = (e) => {
  for (let index = 0; index < buttonshit.length; index++) {
    const element = buttonshit[index];
    if (element.buttonName === e.target.innerText) {
      selectedButton = element
    }
  }

  
}

function getOffset(el) {
  const rect = el.getBoundingClientRect();
  return {
    left: rect.left + window.scrollX,
    top: rect.top + window.scrollY
  };
}

//
</script>

<main>
    <div class="buttonHolder" id="holder">
      {#if vis===true}
        <div class="sexyUnderline" id="coolUnderline" bind:offsetWidth={xPosition} bind:offsetHeight={yPosition} in:moveUnderline="{{xPosDes:500,yPosDes:5,duration:200}}" ></div>
      {/if}
        {#each buttonshit as leButton}
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <div class="carouselButton" id={leButton.blogName} on:click={(e)=>{handleClick(e)}} class:selectedButt={leButton.blogName === selectedButton.blogName}>{leButton.buttonName}</div>
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
  left: 500px;
  bottom: 0;
}

@keyframes moveTo {
  0% {
    left: 0;
    top: 0%
  }

}
</style>
