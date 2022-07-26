<template>
<section>
  <BaseHeader />
  <DiscSection />
</section>
</template>

<script>
import BaseHeader from './components/BaseHeader.vue';
import DiscSection from './components/DiscSection.vue';

export default {
  name: 'App',
  components: {
    BaseHeader,
    DiscSection,
  }
}
</script>

<style lang="scss">
  @import './assets/scss/style.scss';
</style>
