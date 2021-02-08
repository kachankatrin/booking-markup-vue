<template>
  <v-card class="my-7 px-5 py-6 loyalty-card" max-width="710">
    <v-card-title class="d-flex justify-space-between custom-card-title">Loyalty Program</v-card-title>
    <v-divider class="custom-divider"></v-divider>
    <v-card-text class="card-text">
      <v-card-title class="d-flex justify-space-between custom-card-title px-0 loyalty-title">
        <span>7th Heaven rewards</span>
        <span>WE223546</span>
      </v-card-title>
      <v-divider></v-divider>
      <v-card-title class="custom-card-title px-0 mt-7 pb-2"></v-card-title>
    </v-card-text>
  </v-card>
</template>
<script>
export default {
    name: "LoyaltyCard"
}
</script>
<style scoped lang="scss">
.loyalty-card {
  font-size: 12px;
  .custom-card-title {
    padding-top: 2px;
    font-size: 14px;
    font-family: CircularStd-Medium;
    &.loyalty-title {
      max-width: 222px;
      font-size: 12px;
    }
  }
  .custom-divider {
    width: 420px;
    margin-left: -20px;
    max-width: unset;
  }
  .card-text {
    padding-bottom: 0;
  }
}
</style>