<template>
  <div>


    <h3 :style="h4Style">dasd</h3>
    <h2 :style="h3Style">asdas</h2>
    <span v-for="i in 3" :key="i"> {{i}} for test</span> 

    <span v-for="(i,data) in forData" :key="i"> {{data}}</span>


    <div @click="testFunction()" v-for="(i, data) in forData" :key="i">{{data}}</div>

    <Data :propsdata = "forData" />

    <!-- 자식 -->
    <div>
      <h3 @click="$emit('senData', oneroomedata.id)">asdas</h3>
    </div>




    <!-- 부모 -->
    <Data @sendData="hi === true; thisData = $event" />




  </div>
</template>

<script>
export default {
  data() {
    return {
      h4Style: 'color:red',
      h3Style: 'margintTop: 10px',
      forData :[1,2,3,4,5]
    }
  },
  props: {
    propsdata: Array,
  },
  methods: {
    testFunction(){
      let hi = this.forData.map((i)=>{
        return i * 10;
      });

      return hi;
    }
  },
};
</script>

<style>


</style>