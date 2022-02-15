<template>
  <div class="black-bg" v-if="모달창열렸니 === true">
    <div class="white-bg">
      <img :src="원룸들[누른거].image" alt="" />
      <h4>{{ 원룸들[누른거].title }}</h4>
      <span>{{ 원룸들[누른거].price }} 만원</span>
      <p>{{ 원룸들[누른거].content }}</p>
      <Discount />
      <!-- <button @click="모달창열렸니 = false">열고 닫기</button> -->
    </div>
  </div>
</template>

<script>
import Discount from "./ Discount.vue";

export default {
  name: "Modal",
  component: {
    Discount: Discount,
  },
  props: {
    원룸들: Array,
    누른거: Number,
    모달창열렸니: Boolean,
  },
};
</script>

<style>
</style>