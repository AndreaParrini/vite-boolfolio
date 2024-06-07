<script>
import SectionHeader from './components/SectionHeader.vue';
import SectionMain from './components/SectionMain.vue'

export default {
  name: 'App',
  components: {
    SectionHeader,
    SectionMain
  }

}
</script>

<template>
  <SectionHeader></SectionHeader>

  <SectionMain></SectionMain>

  <footer>

  </footer>
</template>

<style scoped></style>
