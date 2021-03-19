<template>
  <header>
    <p>VIP</p>
  </header>
  <div class="main">
    <Home
    @openAlert="openAlert"
    :newMember="newMember"></Home>
  </div>
  <footer>
    <Footer></Footer>
  </footer>
  <div class="alert">
    <Alert
    v-if="isAlertOpened"
    :member="chooseMember"
    @cancel="closeAlert"
    @buy="buyMember"
    ></Alert>
  </div>
  <button class="btn-service">
    <img src="./assets/img/8.svg" alt="">
  </button>
</template>

<script>
import Home from './components/Homepage.vue'
import Footer from './components/Footer.vue'
import Alert from './components/Alert.vue'

export default {
  name: 'App',
  components: {
    Home,
    Footer,
    Alert
  },
  data() {
    return {
      isAlertOpened: false,
      chooseMember: {},
      newMember: {}
    }
  },
  methods: {
    closeAlert() {
      this.isAlertOpened = false;
    },
    openAlert(item) {
      this.isAlertOpened = true;
      this.chooseMember = item;
    },
    buyMember(item) {
      this.newMember = item;
      this.isAlertOpened = false;
    }
  },
}
</script>

<style lang="scss">
@import "./assets/scss/all";
</style>
