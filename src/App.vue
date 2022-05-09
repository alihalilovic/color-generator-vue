<script setup>
  import { ref } from "vue"

  const currentColor = ref("#333333")

  const colorValues = Array.from(Array(10).keys())
  const letterValues = ["A", "B", "C", "D", "E", "F"]
  const allValues = colorValues.concat(letterValues)

  const generateColor = () => {
    let newColor = "#"
    for(let i = 1; i <= 6; i++) {
      newColor += allValues[Math.floor(Math.random() * allValues.length)]
    }

    currentColor.value = newColor
    console.log(allValues);
  }

</script>

<template>
  <div class="container" :style="{ background: currentColor }">
    <div class="color-container">
      <p>Current color: {{ currentColor }}</p>
      <button class="btn" @click="generateColor">Generate color</button>
    </div>
  </div>
</template>

<style>
  body {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: 'Roboto Condensed', sans-serif;
    -webkit-tap-highlight-color: transparent;
  }

  .container {
    width: 100vw;
    height: 100vh;

    transition: 0.5s ease;
  }

  p {
    margin: 0;
    padding: 0;
  }

  .btn {
    border: none;
    outline: none;
    border-radius: 30px;
    padding: 1rem 2rem;
    font-size: 1.2rem;
    font-family: "Roboto Condensed";
    color: white;
    background: rgba(0, 0, 0, 0.5);
    transition: 0.2s ease;
    user-select: none;
  }
  
  .color-container {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
  }

  .color-container > * {
    margin: .5rem;
  }

  .btn:hover {
    cursor: pointer;
    opacity: 0.8;
  }
</style>
