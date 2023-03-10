<script setup>
import { ref } from "vue";
import { StreamBarcodeReader } from "vue-barcode-reader";

const decodedText = ref("");
let streamDisplay = ref(true);
const onLoaded = () => {
  console.log("loaded");
  decodedText.value = "";
};

const onDecode = (text) => {
  decodedText.value = text;
  console.log(text);
  if (decodedText.value != "" && text != null) {
    streamDisplay = false;
  }
};
</script>

<template>
  <StreamBarcodeReader id="streambarcodeid" @decode="onDecode" @loaded="onLoaded"></StreamBarcodeReader>
  <h2 id="qrcodetext" v-show="false">{{ decodedText }}</h2>
</template>


<style scoped>
a {
  color: #42b983;
}
.information {
  margin-top: 100px;
}
</style>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
