<template>
  <div class="discount">
    <h4>지금 결제하면 {{ saleNum }}만원 할인~</h4>
  </div>
</template>

<script>
export default {
  name: "Discount",
  data() {
    return {
      saleNum: 20,
    };
  },
  mounted() {
    this.sale();
  },
  updated() {
    this.sale();
  },
  methods: {
    sale() {
      if (this.saleNum > 0) {
        setInterval(() => {
          this.saleNum--;
        }, 1000);
      } else this.saleNum = 0;
    },
  },
};
</script>

<style>
</style>