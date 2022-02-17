<template>
  <div>
    <transition name="fade">
      <Modal
        @close="모달창열렸니 = false"
        :원룸들="원룸들"
        :누른거="누른거"
        :모달창열렸니="모달창열렸니"
      />
    </transition>

    <div class="menu">
      <a v-for="(item, index) in 메뉴들" :key="index">{{ item }}</a>
    </div>

    <button @click="priceSort()">가격순 정렬</button>
    <button @click="sortBack()">되돌리기</button>

    <Discount v-if="showDiscount === true" />

    <Card
      @openmodal="
        모달창열렸니 = true;
        누른거 = $event;
      "
      v-for="(item, index) in 원룸들"
      :key="index"
      :원룸="원룸들[index]"
    />
  </div>
</template>

<script>
import data from "./oneroome";
import Card from "./Card.vue";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";

export default {
  name: "App",
  data() {
    return {
      showDiscount: false,
      원룸들오리지널: [...data],
      메뉴들: ["Home", "Shop", "About"],
      모달창열렸니: false,
      원룸들: data,
      누른거: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showDiscount = true;
    }, 4000);
  },
  methods: {
    priceSort() {
      this.원룸들.sort(function (a, b) {
        return a.price - b.price;
      });
    },
    sortBack() {
      this.원룸들 = [...this.원룸들오리지널];
    },
  },
  components: {
    Card,
    Discount,
    Modal,
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

.fade-enter-from {
  opacity: 0;
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
  transform: translateY(0px);
}

/* 퇴장 애니메이션 */
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
