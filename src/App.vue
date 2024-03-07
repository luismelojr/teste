<script setup>
import html2canvas from 'html2canvas';
import { ref } from 'vue';

const imageRef = ref('https://storage.googleapis.com/assets.dev.cuco.info/logos/firstbox/adium.png');
async function printScreenAndDownload() {
  const images = document.querySelectorAll('img');

  images.forEach(async img => {
    await fetch(img.getAttribute('src'), { cache: 'no-cache' });
  });
  const canvas = await html2canvas(
    document.querySelector(`#printAqui`),
    {
      logging: true,
      letterRendering: 1,
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
      <img :src="imageRef" alt="" style="width: 320px;">
    </div>
  </div>
</template>