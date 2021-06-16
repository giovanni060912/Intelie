<template>
  <div class="nav">
    <Header />
    <v-parallax
      class="paralax"
      dark
      src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg"
    >
      <v-row align="center" justify="center">
        <v-col class="text-center" cols="12" align="center" justify="center">
          <v-card class="mx-auto card" outlined>
            <Graphic />
            <v-btn
              class="reset col-12 col-md-3 m-0"
              depressed
              color="#1867c0"
              @click="reset"
            >
              Clear Graphic
            </v-btn>
            <v-btn
              class="reset col-12 col-md-3 m-0"
              depressed
              color="#ff5252"
              @click="
                $router.push({
                  path: '/',
                })
              "
            >
              Back
            </v-btn>
          </v-card>
        </v-col>
      </v-row>
    </v-parallax>
  </div>
</template>

<script>
import Header from "../components/header";
import Graphic from "../components/graphic";

export default {
  components: {
    Header,
    Graphic,
  },
  methods: {
    reset() {
      localStorage.clear();
    },
  },
};
</script>

<style>
.paralax {
  width: 100%;
  height: 100vh !important;
  margin: 0;
  padding: 0;
}
.nav {
  width: 100% !important;
  margin: 0;
  height: 0px !important;
  padding: 0;
}
.card {
  margin-top: 10%;
  max-width: 80%;
}
.reset {
  max-width: 50%;
  margin-top: 10px;
  text-align: center;
  font-weight: 500 !important;
  color: #ffff !important;
}
.tabs:hover {
  color: #1867c0;
}
</style>