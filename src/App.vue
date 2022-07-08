<template>
  <div id="app">
    <nav class="navbar navbar-expand-md navbar-dark fixed-top bg-dark">
      <a class="navbar-brand" href="#">App Tilte</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarCollapse"
        aria-controls="navbarCollapse"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarCollapse">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item active">
            <a class="nav-link" href="#"
              >Home <span class="sr-only">(current)</span></a
            >
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Link</a>
          </li>
        </ul>
      </div>
    </nav>
    <main role="main" class="fluid-container m-4">
      <div class="row">
        <div class="col-8">
          <div
            v-for="(record, id) in records"
            :key="record.id"
            class="card mb-3"
            style="max-width: 720px"
            @click="handleFavorite(id)"
          >
            <div class="row g-0">
              <div class="col-md-4">
                <img
                  :src="record.coverUrl"
                  class="img-fluid rounded-start"
                  alt="..."
                />
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">
                    #{{ id }} ~ {{ record.title }} {{ record.year }}
                    {{ record.isFavorite ? "💓" : "" }}
                  </h5>
                  <h6 class="card-title">{{ record.artist }}</h6>
                  <p class="card-text">{{ record.comment }}</p>
                  <p class="card-text">
                    <small class="text-muted">{{ record.pitchforkPos }}</small>
                  </p>
                </div>
              </div>
            </div>
            <div class="card-footer g-0">
              <button
                @click.stop="incrementStock(id)"
                type="button"
                class="btn btn-info"
              >
                [+]
              </button>
              <button
                @click.stop="decrementStock(id)"
                type="button"
                class="btn btn-info mx-4"
              >
                [-]
              </button>
              <small class=""> {{ record.stock }} en Stock </small>
            </div>
          </div>
        </div>
        <div class="col-4">
          <div class="card bg-light mb-3" style="max-width: 18rem">
            <div class="card-header">
              Infos albums (<strong>{{ records.length }}</strong
              >)
            </div>
            <div class="card-body">
              <h5 class="card-title">Option selec:</h5>
              <select
                class="form-select"
                v-model="sortOption"
                @change="reorderRecords"
              >
                <option value="posAsc">Pitchfork Pos ⬆</option>
                <option value="posDesc">Pitchfork Pos ⬇</option>
                <option value="byYear">Année de sortie</option>
              </select>
              <p class="card-text">Some sorting options</p>
              <h5 class="card-title">Filter</h5>
              <div class="form-check form-switch">
                <input
                  class="form-check-input"
                  type="checkbox"
                  id="flexSwitchCheckDefault"
                  v-model="onlyInStock"
                  @change="onlyAvailableFilter"
                />
                <label class="form-check-label" for="flexSwitchCheckDefault"
                  >Que ceux en stock</label
                >
              </div>

              <div></div>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import { records } from "./assets/static/js/allRecords";

export default {
  name: "App",
  components: {},
  data: () => ({
    records,
    onlyInStock: false,
    sortOption: "",
  }),
  methods: {
    incrementStock(id) {
      this.records[id].stock++;
    },
    decrementStock(id) {
      this.records[id].stock--;
    },
    onlyAvailableFilter() {
      if (this.onlyInStock) {
        this.records = this.records.filter((record) => record.stock > 0);
      } else {
        this.records = records;
        console.log("je voudrais à nouveau tous les albums");
      }
      console.log("! changement filtre ", this.onlyInStock);
    },
    reorderRecords() {
      //         /posAsc
      // posDesc
      // byYear

      if (this.sortOption == "posAsc") {
        this.records.sort((a, b) => {
          return a.pitchforkPos - b.pitchforkPos;
        });
      }
      if (this.sortOption == "posDesc") {
        this.records.sort((a, b) => {
          return b.pitchforkPos - a.pitchforkPos;
        });
      }
      if (this.sortOption == "byYear") {
        this.records.sort((a, b) => {
          return +a.year - +b.year;
        });
      }

      console.log("changement tri ", this.sortOption);
    },
    handleFavorite(id) {
      if (this.records[id].isFavorite) {
        this.records[id].isFavorite = false;
      } else {
        this.$set(this.records[id], "isFavorite", true);
      }
      console.log("had to favorite ", id);
    },
  },
  created() {
    console.log("hey Created");
  },
};
</script>
<style lang="scss">
@import "./assets/navbar-top-fixed.css";
@import "../node_modules/bootstrap/scss/bootstrap.scss";

.negatif {
  background-color: rgb(214, 95, 162);
}
</style>
