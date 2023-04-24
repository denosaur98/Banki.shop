<template>
  <div>
    <HeaderSect/>
    <MainSect/>
    <FooterSect/>
  </div>
</template>

<script>
import HeaderSect from '@/components/header/HeaderSect.vue'
import MainSect from '@/components/main/MainSect.vue'
import FooterSect from '@/components/footer/FooterSect.vue'

export default {
  name: 'App',
  components: {
    HeaderSect, MainSect, FooterSect
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  background: #ECEAEA;
}
</style>