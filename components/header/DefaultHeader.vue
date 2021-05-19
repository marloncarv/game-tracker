<template>
  <b-navbar sticky class="header-bg" type="light">
    <b-navbar-brand href="#">
      <img src="~/static/img/logo-horizontal.svg" alt="Logo Game Tracker" />
    </b-navbar-brand>
  </b-navbar>
</template>

<script>
export default {
  name: 'DefaultHeader',
}
</script>

<style scoped>
.header-bg {
  background-color: var(--primario);
  padding-left: 130px;
  padding-right: 130px;
}

@media only screen and (max-width: 768px) {
  .header-bg {
    padding-left: 0;
    padding-right: 0;
    display: flex;
  }

  .header-bg .navbar-brand {
    display: flex;
    justify-content: center;
    width: 100%;
  }
}
</style>
