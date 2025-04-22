<template>
  <div id="qr-code" ref="qrCode"> </div>
</template>

<script setup lang="ts">

import QRCodeStyling from "qr-code-styling";
import {computed, onMounted, onUpdated, ref} from "vue";

const props = defineProps({
  darkMode: {
    type: Boolean,
    default: false
  }
});

const qrCode = computed(() => new QRCodeStyling({
  width: 300,
  height: 300,
  type: "svg",
  data: "https://nydusborn.github.io/dip-slides/",
  qrOptions: {
    errorCorrectionLevel: "H"
  },
  image: "", // TODO make an icon
  dotsOptions: {
    color: props.darkMode ? "#00a5c0" : "#002e6e",
    type: "extra-rounded"
  },
  backgroundOptions: {
    color: "transparent",
  },
  cornersSquareOptions:{
    type: "extra-rounded"
  },
  cornersDotOptions:{
    type: "extra-rounded"
  },
  imageOptions: {
    crossOrigin: "anonymous",
    margin: 20
  }
}));
onMounted(() => {
  qrCode.value.append(document.getElementById("qr-code"));
})
onUpdated(() => {
  document.getElementById("qr-code")?.childNodes[0]?.remove();
  qrCode.value.append(document.getElementById("qr-code"));
})
</script>