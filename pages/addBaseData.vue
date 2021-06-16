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
          <v-card class="mx-auto card">
            <v-form class="form" ref="form" v-model="valid" lazy-validation>
              <span class="span">Type</span>
              <v-select
                class="select text"
                v-model="form.format"
                :options="type"
              ></v-select>
              <span class="span">Times Tamp</span>
              <v-text-field
                class="text space"
                v-model="form.timestamp"
                solo
              ></v-text-field>
              <span class="span">Browser</span>
              <v-select
                class="select text"
                v-model="form.browser"
                :options="browser"
              ></v-select>
              <span class="span">OS</span>
              <v-select
                class="select text"
                v-model="form.os"
                :options="os"
              ></v-select>
              <span class="span">Min Response Time</span>
              <v-text-field
                class="text space"
                v-model="form.minResponseTime"
                solo
              />
              <span class="span">Max Response Time</span>
              <v-text-field
                class="text space"
                v-model="form.maxResponseTime"
                solo
              />
              <v-btn
                class="btn col-12 col-md-3 m-0"
                depressed
                color="#ff5252"
                @click="
                  $router.push({
                    path: '/',
                  })
                "
              >
                Cancel
              </v-btn>
              <v-btn
                class="btn col-12 col-md-3 m-0 send"
                depressed
                color="#1867c0"
                @click="sendForm"
              >
                Send
              </v-btn>
            </v-form>
          </v-card>
        </v-col>
      </v-row>
    </v-parallax>
  </div>
</template>

<script>
import Vue from "vue";
import Header from "../components/header";
import vSelect from "vue-select";
import VueToastr from "@deveodk/vue-toastr";
import "@deveodk/vue-toastr/dist/@deveodk/vue-toastr.css";
import "vue-select/dist/vue-select.css";
Vue.component("v-select", vSelect);
Vue.use(VueToastr, {
  defaultPosition: "toast-bottom-right",
  defaultType: "info",
  timeout: 9000,
});

export default {
  data: () => ({
    loading: false,
    valid: false,
    timestamp: "",
    minResponseTime: "",
    maxResponseTime: "",
    select: null,
    os: ["Linux", "Mac", "Windows"],
    browser: ["Chrome", "Opera", "FireFox", "Edge", "Internet Explorer"],
    type: ["Start", "Stop", "data"],
    form: {
      format: "",
      timestamp: "",
      browser: "",
      os: "",
      minResponseTime: "",
      maxResponseTime: "",
    },
  }),
  components: {
    Header,
  },

  methods: {
    sendForm() {
      const data = JSON.parse(localStorage.getItem("DataListChart")) || [];
      const itemForm = {
        label: this.form.browser,
        borderColor:
          "#" +
          Math.floor(Math.random() * (0xffffff + 1))
            .toString(16)
            .padStart(6, "0"),
        backgroundColor: "transparent",
        data: [this.form.minResponseTime, this.form.maxResponseTime],
      };
      data.push(itemForm);
      localStorage.setItem("DataListChart", JSON.stringify(data));
      this.$toastr("success", "Form sent successfully!");

  //       const hora    = this.form.data.getHours();
  //       const min     = this.form.data.getMinutes();
  //       const seg     = this.form.data.getSeconds();
  //       const mseg    = this.form.data.getMilliseconds();

  //  const timestamp = colectTime (
  //    timestamp(hora,min,seg,mseg)
  //  )
  //  console.log(timestamp);
},
  },
};
</script>

<style>
.container {
  margin: 0;
  padding: 0;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  max-width: 100%;
  background-color: #f1f1f1f1;
  width: 100% !important;
}
.card {
  max-width: 50%;
  padding: 5%;
  margin-top: 5%;
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
.btn {
  margin-top: 10px;
  text-align: center;
  font-weight: 500 !important;
  color: #ffff !important;
}
.select {
  margin-top: 10px;
}
.select input {
  padding: 6px !important;
}
.text div {
  margin-top: 5px;
}
.space {
  margin-bottom: -35px !important;
}
.span {
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
}
@media screen and (max-width: 956px) {
  .send {
    margin-top: 5px !important;
  }
}
</style>