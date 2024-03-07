<script setup>
import html2canvas from 'html2canvas';
async function printScreenAndDownload() {
  const canvas = await html2canvas(
    document.querySelector(`#printAqui`),
    {
      logging: true,
      letterRendering: 1,
      useCORS: true,
      allowTaint: true
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
      <img src="https://storage.googleapis.com/assets.dev.cuco.info/logos/firstbox/adium.png" alt=""
        style="width: 320px;">
    </div>
  </div>
</template>