<script>
import PageHeader from './components/PageHeader.vue'
import MainContent from './components/MainContent.vue'
import PageFooter from './components/PageFooter.vue'

export default {
  components: {
   PageHeader,
   MainContent,
   PageFooter
  }
}
</script>

<template>
  <PageHeader />
  <MainContent />
  <PageFooter />
</template>

<style lang="scss">
@use './styles/general.scss';
</style>
