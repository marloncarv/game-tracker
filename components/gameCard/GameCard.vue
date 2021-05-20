<template>
  <div class="col-xl-4 col-lg-6 col-12">
    <b-card no-body :title="game.title" img-top class="mb-2 game-card">
      <b-img-lazy
        :id="'card-' + game.gameID"
        class="card-img-top"
        :alt="game.title"
        :src="`https://cdn.akamai.steamstatic.com/steam/apps/${game.steamAppID}/header.jpg`"
        @error.native="replaceImg(game.gameID)"
      />
      <div class="card-body">
        <b-card-title class="game-title text-truncate">{{
          game.title
        }}</b-card-title>
        <div class="buttons-and-prices">
          <b-button class="btn btn-detalhes">Detalhes</b-button>
          <div class="ml-auto right-box">
            <div class="prices-container">
              <div class="normal-price">
                <span>$ {{ game.normalPrice }}</span>
              </div>
              <div class="sale-price">
                <span>$ {{ game.salePrice }}</span>
              </div>
            </div>
            <div class="btn btn-discount">
              {{ getPercentDiscount(game.savings) }}
            </div>
          </div>
        </div>
      </div>
    </b-card>
  </div>
</template>

<script>
export default {
  props: {
    game: {
      type: Object,
      default: () => {},
    },
  },

  methods: {
    getPercentDiscount(savings) {
      const number = parseInt(savings)
      return number > 0 ? '-' + number + '%' : 'Grátis'
    },

    replaceImg(id) {
      const img = document.getElementById('card-' + id)
      img.src = require('~/static/img/sem-imagem.jpg')
    },
  },
}
</script>

<style scoped>
.game-card.card {
  background: var(--primario);
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  border-radius: 8px;
}

.card-body {
  padding: 7px 15px 15px 15px;
}

.game-title {
  font-style: normal;
  font-weight: 300;
  font-size: 24px;
  line-height: 33px;
}

.buttons-and-prices {
  margin-top: 15px;
  display: flex;
}

.btn-detalhes {
  border-radius: 8px;
  background: var(--secundario);
  border: 0;
  font-style: normal;
  font-weight: bold;
  font-size: 18px;
  line-height: 21px;
  text-transform: uppercase;
  padding: 9px 15px 9px 15px;
}

.btn-discount {
  min-width: 84px;
  border-radius: 8px;
  background: var(--sucesso);
  border: 0;
  font-style: normal;
  font-weight: bold;
  font-size: 18px;
  line-height: 21px;
  text-transform: uppercase;
  padding: 9px 15px 9px 15px;
  cursor: unset !important;
  color: #fff;
}

.prices-container {
  display: flex;
  flex-direction: column;
  margin-right: 10px;
}

.right-box {
  display: flex;
  align-items: flex-end;
}

.normal-price {
  font-style: normal;
  font-weight: 200;
  font-size: 12px;
  line-height: 14px;
  text-align: right;
  text-decoration-line: line-through;
}

.sale-price {
  font-style: normal;
  font-weight: bold;
  font-size: 18px;
  line-height: 21px;
  text-align: right;
}
</style>
