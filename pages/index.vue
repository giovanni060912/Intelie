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
          <v-card class="mx-auto card" outlined align="center" justify="center">
            <div class="text-center">
              <v-tabs class="tabs" align="center" justify="center">
                <v-tab
                  @click="
                    $router.push({
                      name: 'addBaseData',
                    })
                  "
                  >Add base data</v-tab
                >
                <v-tab
                  @click="
                    $router.push({
                      name: 'dateGraphic',
                    })
                  "
                  >Graphic</v-tab
                >
              </v-tabs>
            </div>
          </v-card>
        </v-col>
      </v-row>
    </v-parallax>
  </div>
</template>
                v-if="data_items.length > 0"

<script>
import Header from "../components/header";

export default {
   data: () => ({
 data_items: []

}),
  components: {
    Header,
  },
//   created() {
// const data  = JSON.parse(localStorage.getItem('DataListChart')) || []
// this.data_items = data
//   }
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-color: #f1f1f1f1;
  width: 100% !important;
  min-width: 100%;
}
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
  margin-top: 21%;
  max-width: 25%;
  padding: 2%;
}
.tabs:hover {
  color: #1867c0;
}
</style>
