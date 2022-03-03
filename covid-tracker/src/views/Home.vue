<template>
  <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate" />

    <DataBoxes :stats="stats" />

    <CountrySelect @get-country="getCountryData" :countries="countries" />

    <button
      @click="clearCountryData"
      v-if="stats.Country"
      class="
        bg-green-700
        text-white
        rounded
        p-3
        mt-10
        focus:outline-none
        hover:bg-green-600
      "
    >
      Clear Country
    </button>
  </main>

  <main v-else class="flex flex-col align-center justify-center text-center">
    <div class="text-gray-500 text-3xl mt-10 mb-6">Fetching Data</div>
  </main>
</template>

<script>
import DataTitle from "@/components/DataTitle";
import DataBoxes from "@/components/DataBoxes";
import CountrySelect from "@/components/CountrySelect";
import axios from "axios";

export default {
  name: "Home",
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect,
  },
  data() {
    return {
      loading: true,
      title: "Global",
      dataDate: "",
      stats: {},
      countries: [],
    };
  },
  methods: {
    async fetchCovidData() {
      try {
        const res = await fetch("https://api.covid19api.com/summary");

        const data = await res.json();

        // const res = await axios.get("https://api.covid19api.com/summary");
        // const data = await res.data.Countries
        return data;
      } catch {
        console.log("Axios error");
      }
    },
    getCountryData(country) {
      this.stats = country;
      this.title = country.Country;
    },
    async clearCountryData() {
      try {
        this.loading = true;
        const data = await this.fetchCovidData();
        this.title = "Global";
        this.stats = data.Global;
        this.loading = false;
      } catch {
        console.log("clear error");
      }
    },
  },
  async created() {
    try {
      const data = await this.fetchCovidData();

      console.log(data);

      this.dataDate = data.Date;
      this.stats = data.Global;
      this.countries = data.Countries;
      this.loading = false;
    } catch {
      console.log("created error");
    }
  },
};
</script>
