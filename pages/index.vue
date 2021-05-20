<template>
  <div class="container-fluid">
    <page-title title="Ofertas" />
    <default-filters
      ref="filters-component"
      @search-change="filterSearch"
      @change-sort="changeSorting"
      @loading="loading = true"
    />
    <div v-show="loading" class="row mt-4">
      <div class="col-12 loading-spinner">
        <b-spinner class="mr-2" label="Loading..."></b-spinner>
        Carregando...
      </div>
    </div>
    <div class="row mt-4">
      <game-card v-for="(game, index) in gamesList" :key="index" :game="game" />
    </div>
    <div class="row mt-4 mb-4">
      <div class="col-12">
        <button class="btn btn-load" @click="loadMore" :disabled="loading">
          Carregar mais
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import PageTitle from '~/components/common/PageTitle.vue'
import DefaultFilters from '~/components/filters/DefaultFilters.vue'
import GameCard from '~/components/gameCard/GameCard.vue'

export default {
  components: {
    PageTitle,
    DefaultFilters,
    GameCard,
  },

  data() {
    return {
      gamesList: [],
      currentPage: 0,
      loading: false,
    }
  },

  computed: {
    search() {
      return this.$refs['filters-component'].search || ''
    },

    sortBy() {
      return this.$refs['filters-component'].selected || ''
    },
  },

  mounted() {
    this.getGameDeals()
  },

  methods: {
    getGameDeals() {
      const url = `https://www.cheapshark.com/api/1.0/deals?pageNumber=${this.currentPage}&sortBy=${this.sortBy.value}&desc=${this.sortBy.desc}&title=${this.search}&pageSize=12&storeID=1&onSale=1&AAA=1`
      this.loading = true
      this.$axios
        .get(url)
        .then((res) => {
          if (this.currentPage === 0) {
            this.gamesList = res.data
          } else {
            this.gamesList = this.gamesList.concat(res.data)
          }
          this.loading = false
        })
        .catch(console.error)
    },

    loadMore() {
      this.currentPage += 1
      this.getGameDeals()
    },

    filterSearch() {
      this.currentPage = 0
      this.getGameDeals()
    },

    changeSorting() {
      this.currentPage = 0
      this.getGameDeals()
    },
  },
}
</script>

<style scoped>
.btn-load {
  background: #0b1641;
  border-radius: 8px;
  font-style: normal;
  font-weight: 200;
  font-size: 18px;
  line-height: 21px;
  display: flex;
  align-items: center;
  text-align: center;
  color: #fff;
  padding: 15px 135px 15px 135px;
  margin: 0 auto;
}

.loading-spinner {
  align-items: center;
  display: flex;
  justify-content: center;
}

@media only screen and (max-width: 768px) {
  .btn-load {
    padding: 15px 85px 15px 85px;
  }
}
</style>
