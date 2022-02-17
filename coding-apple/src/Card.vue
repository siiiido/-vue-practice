<template>
  <div>
    <img :src="원룸.image" alt="" class="room-image" />
    <h4 @click="send()" style="cursor: pointer">{{ 원룸.title }}</h4>
    <p>{{ 원룸.price }}</p>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    원룸: Object,
  },
  methods: {
    send() {
      this.$emit("openmodal", this.원룸.id);
    },
  },
};
</script>

<style>
</style>