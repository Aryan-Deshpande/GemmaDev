<template>
  <div class="build-container">

    <div class="chat">
      <!-- Make a rectangle div where text can be entered from the text prompt below -->
      Hey there, I'm where the answer is supposed to be
      <h3>{{ chatval }}</h3>
    </div>

    <div class="Wrapper">
      <div class="Input">
        <input type="text" id="input" class="Input-text">
        <label for="input" class="Input-label"></label>
      </div>
    </div>
    
  </div>
</template>

<script setup>

import { ref } from 'vue';

const inputText = ref('');
const chatval = ref('');

function getval() {
  chatval.value = inputText.value;
}
</script>

<style>

@import url('https://fonts.googleapis.com/css?family=Dosis');

:root {
  /* generic */
  --gutterSm: 0.4rem;
  --gutterMd: 0.8rem;
  --gutterLg: 1.6rem;
  --gutterXl: 2.4rem;
  --gutterXx: 7.2rem;
  --colorPrimary400: #ffffff;
  --colorPrimary600: #b6b6b6;
  --colorPrimary800: #717171;
  --fontFamily: "Dosis", sans-serif;
  --fontSizeSm: 1.2rem;
  --fontSizeMd: 1.6rem;
  --fontSizeLg: 2.1rem;
  --fontSizeXl: 2.8rem;
  --fontSizeXx: 3.6rem;
  --lineHeightSm: 1.1;
  --lineHeightMd: 1.8;
  --transitionDuration: 300ms;
  --transitionTF: cubic-bezier(0.645, 0.045, 0.355, 1);
  
  /* floated labels */
  --inputPaddingV: var(--gutterMd);
  --inputPaddingH: var(--gutterLg);
  --inputFontSize: var(--fontSizeLg);
  --inputLineHeight: var(--lineHeightMd);
  --labelScaleFactor: 0.8;
  --labelDefaultPosY: 50%;
  --labelTransformedPosY: calc(
    (var(--labelDefaultPosY)) - 
    (var(--inputPaddingV) * var(--labelScaleFactor)) - 
    (var(--inputFontSize) * var(--inputLineHeight))
  );
  --inputTransitionDuration: var(--transitionDuration);
  --inputTransitionTF: var(--transitionTF);
}

*,
*::before,
*::after {
  box-sizing: border-box;
}

.Wrapper {
  flex: 0 0 80%;
  max-width: 40%;
}

.Title {
  margin: 0 0 var(--gutterXx) 0;
  padding: 0;
  color: #000000;
  font-size: var(--fontSizeXx);
  font-weight: 400;
  line-height: var(--lineHeightSm);
  text-align: center;
  text-shadow: -0.1rem 0.1rem 0.2rem var(--colorPrimary800);
}

.Input {
  position: relative;
}

.Input-text {
  display: block;
  margin: 0;
  padding: 5px;
  color: inherit;
  width: 185%;
  height: 10%;
  font-family: inherit;
  font-size: var(--inputFontSize);
  font-weight: inherit;
  line-height: var(--inputLineHeight);
  border: none;
  color: #000000;
  border-radius: 0.4rem;
  transition: box-shadow var(--transitionDuration);
  
}

.Input-text::placeholder {
  color: #000000;
}

.Input-text:focus {
  outline: none;
  box-shadow: 0.2rem 0.8rem 1.6rem var(--colorPrimary600);
}

.Input-label {
  display: block;
  position: absolute;
  bottom: 50%;
  left: 1rem;
  color: #000000;
  font-family: inherit;
  font-size: var(--inputFontSize);
  font-weight: inherit;
  line-height: var(--inputLineHeight);
  opacity: 0;
  transform: 
    translate3d(0, var(--labelDefaultPosY), 0)
    scale(1);
  transform-origin: 0 0;
  transition:
    opacity var(--inputTransitionDuration) var(--inputTransitionTF),
    transform var(--inputTransitionDuration) var(--inputTransitionTF),
    visibility 0ms var(--inputTransitionDuration) var(--inputTransitionTF),
    z-index 0ms var(--inputTransitionDuration) var(--inputTransitionTF);
}

.Input-text:placeholder-shown + .Input-label {
  visibility: hidden;
  z-index: -1;
}

.Input-text:not(:placeholder-shown) + .Input-label,
.Input-text:focus:not(:placeholder-shown) + .Input-label {
  visibility: visible;
  z-index: 1;
  opacity: 1;
  transform:
    translate3d(0, var(--labelTransformedPosY), 0)
    scale(var(--labelScaleFactor));
  transition:
    transform var(--inputTransitionDuration),
    visibility 0ms,
    z-index 0ms;
}


.build-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.chat {
  text-align: center;
  background-color: grey;
  color: white;
  padding: 10px;
  border-radius: 3px;
  margin: 10px;
  width: 100%;
  height: 200%;
  max-width: 500px; /* Adjust the maximum width as needed */
  height: 200px; /* Adjust the height as needed */
  overflow-y: scroll;
  scroll-behavior: smooth;
}

.input-wrapper {
  display: flex;
  align-items: center;
}

.input-text {
  flex: 1;
  margin-right: 10px;
}

</style>
