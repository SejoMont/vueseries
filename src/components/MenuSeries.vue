<template>
  <div class="fixed-top text-start" style="max-width: inherit; margin: auto">
    <nav class="navbar navbar-expand-lg bg-body-tertiary">
      <div class="container-fluid">
        <a class="navbar-brand" href="/">Navbar</a>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNav"
          aria-controls="navbarNav"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav">
            <li class="nav-item">
              <router-link class="nav-link active" aria-current="page" to="/"
                >Home</router-link
              >
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/nuevo">Nuevo Personaje</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/modificar"
                >Modificar Personaje</router-link
              >
            </li>
            <li class="nav-item dropdown">
              <button
                class="btn dropdown-toggle"
                data-bs-toggle="dropdown"
                aria-expanded="false"
              >
                Series
              </button>
              <ul class="dropdown-menu">
                <li v-for="serie in series" :key="serie">
                  <router-link class="dropdown-item" :to="'/serie/'+ serie.idSerie">{{serie.nombre}}</router-link>
                </li>
              </ul>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
import Global from "./../Global";
import axios from "axios";
export default {
  name: "MenuSeries",
  data() {
    return {
      series: [],
    };
  },
  mounted() {
    var request = "api/series";
    var url = Global.urlApiSeries + request;

    axios.get(url).then((response) => {
        this.series = response.data
    })
  },
};
</script>