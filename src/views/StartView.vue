<template>
    <div class="scan-page">
      <div class="scan-button" @click="startScan">
        <v-icon color="white">mdi-camera</v-icon>
        <span>Scan</span>
      </div>
      <qrcode-stream ref="scanner" @decode="onDecode" :camera="camera"></qrcode-stream>
    </div>
  </template>
  
  <script>
  import QrcodeStream from 'vue-qrcode-reader';
  
  export default {
    components: {
      QrcodeStream
    },
    data() {
      return {
        camera: null
      }
    },
    methods: {
        startScan() {
  this.$nextTick(() => {
    this.$refs.scanner.start();
  });
},
      onDecode(result) {
        console.log(result);
      }
    }
  };
  </script>
  
  <style>
  .scan-page {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100%;
  }
  
  .scan-button {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 200px;
    height: 200px;
    border-radius: 50%;
    background-color: #007bff;
    color: white;
    font-size: 2em;
    cursor: pointer;
  }
  
  .scan-button:hover {
    background-color: #0062cc;
  }
  </style>
  