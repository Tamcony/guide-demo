<script setup>
import HelloWorld from './components/HelloWorld.vue'
import Driver from "driver.js";
import { ref, onMounted } from 'vue'

const img = ref()
const text = ref()
const init = () => {
  const driver = new Driver({
    animate: true,
    allowClose: false,
    // opacity: 0,
    className: 'scoped-class', // className to wrap driver.js popover
    // animate: true,  // Animate while changing highlighted element
    // opacity: 0.75,  // Background opacity (0 means only popovers and without overlay)
    // padding: 10,    // Distance of element from around the edges
    // allowClose: true, // Whether clicking on overlay should close or not
    // overlayClickNext: false, // Should it move to next step on overlay click
    doneBtnText: '结束', // Text on the final button
    closeBtnText: '关闭', // Text on the close button for this step
    nextBtnText: '下一步', // Next button text for this step
    prevBtnText: '上一步', // Previous button text for this step
    // showButtons: false, // Do not show control buttons in footer
    // keyboardControl: true, // Allow controlling through keyboard (escape to close, arrow keys to move)
    // scrollIntoViewOptions: {}, // We use `scrollIntoView()` when possible, pass here the options for it if you want any
    // onHighlightStarted: (Element) { }, // Called when element is about to be highlighted
    // onHighlighted: (Element) { }, // Called when element is fully highlighted
    // onDeselected: (Element) { }, // Called when element has been deselected
    // onReset: (Element) { },        // Called when overlay is about to be cleared
    // onNext: (Element) => { },      // Called when moving to next step on any step
    // onPrevious: (Element) => { },  // Called when moving to next step on any step
  })
  driver.defineSteps([
    {
      element: img.value,
      popover: {
        title: '第一步',
        description: '这是两个图片',
        position: 'bottom',
      }
    },
    {
      element: text.value,
      popover: {
        title: '第二步',
        description: '这是一段文字',
        position: 'right',
      }
    }
  ])
  driver.start()
}
onMounted(() => {
  init()
})
</script>

<template>
  <div ref="img">
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <p ref="text">11111</p>
  <HelloWorld msg="Vite + Vue" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
