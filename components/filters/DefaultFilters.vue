<template>
  <div class="row filters-content">
    <div class="col-md-4 col-7">
      <b-input-group class="search-input-group">
        <b-input-group-text>
          <b-icon icon="search" />
        </b-input-group-text>
        <b-form-input
          class="text-search filters-text"
          placeholder="Procurar"
          type="text"
        />
      </b-input-group>
    </div>
    <div class="col-5 col-md-8">
      <div class="filter-dropdown-box float-right">
        <label class="filter-dropdown-label"> Ordenar por: </label>
        <b-dropdown class="filter-select filters-text" :text="selected">
          <b-dropdown-item
            v-for="item in options"
            :key="item"
            @click="selectFilter(item)"
          >
            {{ item }}
          </b-dropdown-item>
        </b-dropdown>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DefaultFilters',
  data() {
    return {
      selected: '% de Desconto',
      options: ['% de Desconto', 'Maior preço', 'Menor preço', 'Título'],
    }
  },

  methods: {
    selectFilter(filter) {
      this.selected = filter
    },
  },
}
</script>

<style scoped>
.filters-content {
  margin-top: 22px;
}

.text-search {
  background-color: var(--primario);
  border: 0;
  border-radius: 8px;
  padding-top: 24px;
  padding-bottom: 24px;
  min-height: 51px;
}

.input-group.search-input-group .input-group-text {
  border: 0;
  border-radius: 8px;
  background-color: var(--primario);
  color: #dadada;
  border-top-right-radius: 0;
  border-bottom-right-radius: 0;
  padding-top: 15px;
  padding-bottom: 15px;
}

.input-group.search-input-group .input-group-text .b-icon.bi {
  font-size: 18px;
}

.filter-dropdown-label {
  font-style: normal;
  font-weight: bold;
  font-size: 18px;
  line-height: 21px;
}

.filter-select {
  width: auto;
  background: var(--primario);
  border: 0;
  border-radius: 8px;
  margin-left: 20px;
}

.filter-select >>> .btn-secondary,
.filter-select >>> .dropdown-menu {
  background: var(--primario);
  border: 0;
  background: var(--primario);
  border: 0;
  border-radius: 8px;
  font-weight: 200;
  font-size: 18px;
  line-height: 21px;
  padding-top: 15px;
  padding-bottom: 15px;
  font-style: normal;
  min-width: 180px;
}

.filter-select >>> .dropdown-menu {
  margin-top: -5px;
}

.filter-select >>> .dropdown-menu .dropdown-item {
  color: #fff;
}

.filter-select >>> .dropdown-menu .dropdown-item:hover,
.filter-select >>> .dropdown-menu .dropdown-item:focus {
  color: var(--secundario);
  background: inherit;
}

.filters-text {
  font-weight: 200;
  font-size: 18px;
  line-height: 21px;
  color: #fff;
}

@media only screen and (max-width: 768px) {
  .filter-select {
    margin-left: 0;
    width: 100%;
  }

  .filters-text {
    font-size: 0.9rem;
  }

  .filter-dropdown-box {
    width: 100%;
  }

  .filter-select >>> .btn-secondary,
  .filter-select >>> .dropdown-menu {
    min-width: 100%;
    font-size: 0.7rem;
  }

  .filter-dropdown-label {
    float: left;
    margin-top: -29px;
    width: 100%;
    text-align: center;
    font-size: 0.7rem;
  }
}
</style>
