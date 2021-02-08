<template>
  <v-card class="mx-8 my-7 px-5 py-6 pricing-card" max-width="420">
    <v-card-title class="d-flex justify-space-between custom-card-title">Price Details</v-card-title>
    <v-divider class="custom-divider"></v-divider>
    <v-card-text class="card-text">
      <v-card-title class="d-flex justify-space-between custom-card-title px-0 trips-title">
        <span>Round trip</span>
        <span>|</span>
        <span>2 travelers</span>
      </v-card-title>

      <ul>
        <li
          v-for="(value, name) in priceDetails"
          :key="name"
          class="d-flex justify-space-between my-5"
        >
          <span class="d-flex align-center">{{name}}<v-icon class="ml-2 mt-1" x-small color="#B0B3C2" v-show="name === 'Taxes'">mdi-help-circle-outline</v-icon></span>
          <span :style="value === 'Free' ? 'color: #57D1AA; font-family: CircularStd-Bold;' : ''">{{value}}</span>
        </li>
      </ul>
      <v-divider></v-divider>
      <v-card-title class="custom-card-title px-0 mt-7 pb-2">
        <ul>
          <li v-for="(value, name) in price" :key="value" class="d-flex justify-space-between">
            <span>{{name}}</span>
            <span>{{value}}</span>
          </li>
        </ul>
        <!-- <span>{{}}</span> -->
      </v-card-title>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: "PriceDetailsCard",
  data() {
    return {
      colors: {
        "Kathryn Pena": "rgba(249,104,120,1)",
        "Lee Nguyen": "rgba(160,196,247,1)"
      },
      priceDetails: {
        "Total rate": "$14.50",
        Taxes: "$25.50",
        "SoldoutNight Fee": "Free"
      },
      price: {
        "Total Price": "$684.75"
      }
    };
  },
};
</script>

<style scoped lang="scss">
.pricing-card {
  font-size: 12px;
  .custom-card-title {
    padding-top: 2px;
    font-size: 14px;
    font-family: CircularStd-Medium;
    color: rgba(41,41,73,1);
    &.trips-title {
        max-width: 165px;
        font-size: 13px;
    }
    ul {
      width: 100%;
      li {
        width: 100%;
      }
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
  .custom-chip {
    font-family: CircularStd-Medium;
    font-size: 12px;
  }
}
.v-application {
  ul {
    padding-left: 0;
  }
}
</style>