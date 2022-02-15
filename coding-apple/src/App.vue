<template>
  <div>
    <div class="menu">
      <a v-for="a in 메뉴들" :key="a">{{ a }} </a>
    </div>
    <Modal :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니" />

    <Card :원룸="원룸들[i]" v-for="(작명, i) in 원룸들" :key="작명" />
  </div>
</template>

<script>
import data from "../src/oneroome";
import Modal from "./Modal.vue";
import Card from "./Card.vue";

export default {
  name: "App",
  data() {
    return {
      메뉴들: ["Home", "Shop", "About"],
      products: ["역산동 원룸", "천호동 원룸", "마포구 원룸"],
      price: ["60", "120", "70"],
      신고수: [0, 0, 0],
      모달창열렸니: false,
      원룸들: data,
      누른거: 0,
    };
  },
  methods: {
    increase() {
      this.신고수 += 1;
    },
  },
  components: {
    Modal: Modal,
    Card,
  },
};
</script>

<style>
.room-image {
  width: 100%;
  margin-top: 40px;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>

