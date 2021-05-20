<template>
  <div class="footer mt-2">
    <img
      src="~/static/img/logo-icone.svg"
      class="ml-auto mr-auto"
      alt="Logo Game Tracker"
    />
    <p class="footer-text">
      © 2021, Game Tracker Inc. Todos os direitos reservados. Nulla facilisi.
      Etiam sagittis congue tempor. Pellentesque habitant morbi tristique
      senectus et netus et malesuada fames ac turpis egestas. Suspendisse eu
      velit et ante luctus egestas. Aenean sed nisi tellus. Duis non ornare
      libero. Quisque suscipit maximus nisi, in gravida felis. Cras ornare
      mauris ac nisi congue, ut condimentum sem tincidunt. Phasellus semper
      tellus malesuada turpis gravida cursus. Duis nec eleifend nunc, vitae
      finibus elit. Aliquam eget diam vitae purus suscipit viverra.
    </p>
    <b-list-group horizontal class="footer-links-list">
      <b-list-group-item>Termos de Serviço</b-list-group-item>
      <b-list-group-item>Política de Privacidade</b-list-group-item>
      <b-list-group-item>Trabalhe conosco</b-list-group-item>
      <b-list-group-item>Contato</b-list-group-item>
    </b-list-group>
  </div>
</template>

<style scoped>
.footer {
  background: var(--primario);
  padding: 60px 130px 60px 130px;
  display: flex;
  align-items: center;
  flex-direction: column;
}

.footer-text {
  font-style: normal;
  font-weight: 300;
  font-size: 14px;
  line-height: 180%;
  margin-top: 32px;
}

.footer-links-list {
  align-self: flex-start;
}

.footer-links-list .list-group-item {
  background: none;
  border: 0;
  padding-right: 23px;
  padding-left: 23px;
  cursor: pointer;
}

.footer-links-list .list-group-item:first-child {
  padding-left: 0;
}

@media only screen and (max-width: 768px) {
  .footer {
    padding: 22px 8px 15px 8px;
  }

  .footer-text {
    text-align: center;
    font-style: normal;
    font-weight: 300;
    line-height: 150%;
    margin-top: 15px;
  }

  .footer-links-list {
    align-self: center;
  }

  .footer-links-list.list-group-horizontal {
    flex-direction: column;
    text-align: center;
  }

  .footer-links-list .list-group-item:first-child {
    padding-left: 23px;
  }
}
</style>
