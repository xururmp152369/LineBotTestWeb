<template>
  <RegiestForm 
  v-bind:profile="profile" />
</template>
<script>
import RegiestForm from "./components/RegiestForm.vue";
export default {
  name: "App",
  components: {
    RegiestForm,
  },
  data() {
    return {
      msg: "",
      profile : {} 
    };
  },
  beforeCreate() {
    // eslint-disable-next-line no-unused-vars
    window.liff
      .init({
        liffId: "1655808021-VQ5ZB376", // Use own liffId
      })
      .then(() => {
        // Start to use liff's api
        this.getProfile();
        console.log("Complete");
      })
      .catch((err) => {
        console.log(err.code, err.message);
      });
  },
  methods: {
    getProfile: function () {
      window.liff
        .getProfile()
        .then((profile) => {
          this.profile = profile;
        })
        .catch((err) => {
          console.log(err.code, err.message);
        });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<!--ngrok http -host-header=localhost 8082-->