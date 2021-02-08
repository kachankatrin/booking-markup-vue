<template>
  <v-app id="booking-app">
    <v-main class="mx-auto">
      <div>
        <booking-card-small />
        <luggage-card />
        <price-details-card />
      </div>
      <div>
        <booking-details-card />
        <guest-information />
        <loyalty-card />
      </div>
    </v-main>
  </v-app>
</template>

<script>
import BookingCardSmall from "./components/BookingCardSmall";
import LuggageCard from "./components/LuggageCard";
import PriceDetailsCard from "./components/PriceDetailsCard";
import LoyaltyCard from "./components/LoyaltyCard";
import BookingDetailsCard from "./components/DetailedInfo/BookingDetailsCard";
import GuestInformation from "./components/DetailedInfo/GuestInformation";

export default {
  name: "App",

  components: {
    BookingCardSmall,
    LuggageCard,
    PriceDetailsCard,
    LoyaltyCard,
    BookingDetailsCard,
    GuestInformation
  }
};
</script>

<style lang="scss">
* {
  list-style: none;
}
#booking-app {
   background: #e5e5e5;
}
.v-application {
  font-family: CircularStd-Book;
  ul {
    padding-left: 0;
  }
}
.v-application-wrap {
  min-height: unset;
}
.v-main__wrap {
  display: flex;
}
.card-subtitle {
  font-family: CircularStd-Book;
}
.theme--light.v-card > .v-card__text {
  color: #7b819a;
}
@font-face {
  font-family: CircularStd-Medium;
  src: url("./fonts/CircularStd/CircularStd-Medium.ttf");
}
@font-face {
  font-family: CircularStd-Book;
  src: url("./fonts/CircularStd/CircularStd-Book.ttf");
}
@font-face {
  font-family: CircularStd-Bold;
  src: url("./fonts/CircularStd/CircularStd-Bold.ttf");
}
</style>
