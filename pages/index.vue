<template>
  <div class="container-fluid">
    <page-title title="Ofertas"></page-title>
    <default-filters></default-filters>
  </div>
</template>

<script>
import PageTitle from '~/components/common/PageTitle.vue'
import DefaultFilters from '~/components/filters/DefaultFilters.vue'

export default {
  components: {
    PageTitle,
    DefaultFilters,
  },
}
</script>

<style scoped></style>
