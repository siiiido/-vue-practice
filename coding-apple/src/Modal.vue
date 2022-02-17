<template>
  <div class="black-bg" v-if="모달창열렸니 === true">
    <div class="white-bg">
      <img :src="원룸들[누른거].image" alt="" />
      <h4>{{ 원룸들[누른거].title }}</h4>
      <p>{{ 원룸들[누른거].content }}</p>
      <!-- <input v-model="month" /> -->
      <input @input="month = $event.target.value" />

      <p>{{ month }} 개월 선택함</p>
      <p>{{ month }}개월은 {{ month * 원룸들[누른거].price }}입니다.</p>
      <button @click="closeBtn()">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: {
    원룸들: Object,
    누른거: Number,
    모달창열렸니: Boolean,
  },
  data() {
    return {
      month: 1,
    };
  },
  methods: {
    closeBtn() {
      this.$emit("close");
    },
  },
  beforeUpdate() {
    if (this.month == 2) {
      alert("2개월 넘 작아 안팔랭");
      this.month = 0;
    }
  },
  watch: {
    month(a, b) {
      if (isNaN(a)) {
        alert("only number");
        this.month = "";
      } else if (b >= 13) {
        alert("over 13");
        this.month = "";
      }
    },
  },
};
</script>

<style>
</style>