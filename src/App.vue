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
          <div class="card mb-3">
            <div class="row no-gutters">
              <div class="col-m-4 m-2">
                <img
                  height="150px"
                  src="https://www.terreseteaux.fr/images/resized/error.png?format=serviceThumbnail&width=280&height=280&size=1&cover=true&extension=jpeg"
                  alt="..."
                />
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">artist</h5>
                  <p class="card-text">title (year)</p>
                  <p class="card-text"></p>
                  <p class="card-text">✨ FAVORI ✨</p>
                </div>
              </div>
            </div>

            <div class="card-footer">
              <button type="button" class="btn btn-info">[+]</button>
              <button type="button" class="btn btn-info mx-4">[-]</button>
              <small class="text-white"> en Stock </small>
            </div>
          </div>
        </div>
        <div class="col-4">
          <div class="card bg-light mb-3" style="max-width: 18rem;">
            <div class="card-header">Infos albums (<strong></strong>)</div>
            <div class="card-body">
              <h5 class="card-title">Option selec:</h5>
              <select class="custom-select">
                <option value="posAsc">Pitchfork Pos ⬆</option>
                <option value="posDesc">Pitchfork Pos ⬇</option>
                <option value="byYear">Année de sortie</option>
              </select>
              <p class="card-text">Some sorting options</p>
              <h5 class="card-title">Filter</h5>
              <div class="custom-control custom-switch">
                <input
                  type="checkbox"
                  class="custom-control-input"
                  id="customSwitch1"
                />
                <label class="custom-control-label" for="customSwitch1"
                  >Que ceux disponible</label
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
    records
  }),
  methods: {},
  created() {
    console.log("hey Created");
  }
};
</script>
<style lang="scss">
@import "./assets/navbar-top-fixed.css";
@import "../node_modules/bootstrap/scss/bootstrap.scss";

.negatif {
}
</style>
