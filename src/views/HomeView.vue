<template>
  <qrcodescanner/>
</template>

<script>
  import Qrcodescanner from '@/components/Qrcodescanner.vue';
  export default {
    name: 'Home',

    components: {
      qrcodescanner: Qrcodescanner
    },
  }
</script>


