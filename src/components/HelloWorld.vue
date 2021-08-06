<template>
  <div class="showdata container">
    <div class="search_box">
      <span>Please input address</span>
      <input type="text" v-model="keyword" class="input" />
    </div>
    <table class="table table_border">
      <thead>
        <tr>
          <td>sno</td>
          <td>sna</td>
          <td>tot</td>
          <td>sarea</td>
          <td>mday</td>
          <td>lat</td>
          <td>lng</td>
          <td>ar</td>
          <td>sareaen</td>
          <td>snaen</td>
          <td>aren</td>
          <td>bemp</td>
          <td>srcUpdateTime</td>
          <td>updateTime</td>
          <td>infoTime</td>
          <td>infoDate</td>
        </tr>
      </thead>
      <tr v-for="loan in loanssearch" :key="loan">
        <td>{{ loan.sno }}</td>
        <td>{{ loan.sna }}</td>
        <td>{{ loan.tot }}</td>
        <td>{{ loan.sarea }}</td>
        <td>{{ loan.mday }}</td>
        <td>{{ loan.lat }}</td>
        <td>{{ loan.lng }}</td>
        <td>{{ loan.ar }}</td>
        <td>{{ loan.sareaen }}</td>
        <td>{{ loan.snaen }}</td>
        <td>{{ loan.aren }}</td>
        <td>{{ loan.bemp }}</td>
        <td>{{ loan.srcUpdateTime }}</td>
        <td>{{ loan.updateTime }}</td>
        <td>{{ loan.infoTime }}</td>
        <td>{{ loan.infoDate }}</td>
        <!-- <td v-for="loa in loan" :key="loa">{{ loa }}</td> -->
      </tr>
    </table>

    <h2 v-if="isShowTip">404 error</h2>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      loans: [],
      keyword: "",
    };
  },
  created() {
    // Simple GET request using fetch
    fetch(
      "https://tcgbusfs.blob.core.windows.net/dotapp/youbike/v2/youbike_immediate.json"
    )
      .then((response) => response.json())
      .then((data) => (this.loans = data));
  },
  computed: {
    loanssearch() {
      return this.loans.filter((loan) => loan.ar.indexOf(this.keyword) > -1);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
