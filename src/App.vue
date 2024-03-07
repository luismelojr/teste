<script setup>
import html2canvas from 'html2canvas';
import { ref } from 'vue';
// import fetch from 'node-fetch'
// const response = await fetch('https://storage.googleapis.com/assets.dev.cuco.info/logos/firstbox/adium.png');
// image_base64 = (await response.buffer()).toString('base64');

// const imageRef = ref(`data:image/png;base64,${image_base64}`);
const imageRef = ref('https://storage.googleapis.com/assets.dev.cuco.info/logos/firstbox/adium.png');
// const imageRef = ref('https://s2-techtudo.glbimg.com/L9wb1xt7tjjL-Ocvos-Ju0tVmfc=/0x0:1200x800/984x0/smart/filters:strip_icc()/i.s3.glbimg.com/v1/AUTH_08fbf48bc0524877943fe86e43087e7a/internal_photos/bs/2023/q/l/TIdfl2SA6J16XZAy56Mw/canvaai.png');
async function printScreenAndDownload() {
  const canvas = await html2canvas(
    document.querySelector(`#printAqui`),
    {
      logging: true,
      letterRendering: 1,
      useCORS: true,
    }
  )

  const link = document.createElement('a')
  link.href = canvas.toDataURL('image/png')
  link.download = 'cupom.png'

  document.body.appendChild(link)
  link.click()

  document.body.removeChild(link)
}
</script>

<template>
  <div>
    <h1>Teste</h1>
    <button @click="printScreenAndDownload">Print</button>
    <div id="printAqui">
      <h2>Print me</h2>
      <img :src="`${imageRef}?time=${new Date().valueOf()}`" crossorigin="anonymous" alt="" style="width: 320px;">
    </div>
  </div>
</template>