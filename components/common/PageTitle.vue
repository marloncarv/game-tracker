<template>
  <div class="row">
    <div class="col-12">
      <h1 class="page-title">{{ title }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PageTitle',
  props: {
    title: {
      type: String,
      default: () => 'Ofertas',
    },
  },
}
</script>

<style scoped>
.page-title {
  margin-top: 45px;
  font-style: normal;
  font-weight: 300;
  font-size: 36px;
  line-height: 42px;
}

@media only screen and (max-width: 768px) {
  .page-title {
    text-align: center;
    margin-top: 16px;
  }
}
</style>
