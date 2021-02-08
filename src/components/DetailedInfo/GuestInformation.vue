<template>
  <v-card class="mx-auto my-7 px-0 pt-6 guests-card" max-width="710">
    <v-card-title class="d-flex justify-space-between custom-card-title mx-5">Guest Information</v-card-title>
    <v-divider class="custom-divider"></v-divider>
    <v-card-text class="card-text pa-0">
      <ul>
        <v-card
          v-for="(guest) in guests"
          :key="guest.name"
          class="px-5 pr-9"
          style="box-shadow: none"
        >
          <single-guest :guest="guest" :messengersLogos="messengersLogos" :icon="icon" />
          <v-divider></v-divider>
        </v-card>
      </ul>
    </v-card-text>
  </v-card>
</template>

<script>
import SingleGuest from "./SingleGuest";
export default {
  name: "GuestInformation",
  components: { SingleGuest },
  data() {
    return {
      icon: "mdi-account-circle",
      guests: [
        {
          name: "Mrs. Kathryn Pena",
          email: "kathrynpena@ibm.com",
          tel: "+380 66 255 33 67",
          messengersLogos: {
            whatsapp: require("../../assets/whatsapp.svg"),
            telegram: require("../../assets/telegram.svg")
          },
          info: {
            "Passport Number": "FJ714612",
            "Passport Country": "Ukraine",
            "Passport Expiration": "May 01, 2020",
            Nationality: "Ukraine",
            "Date of Birth": "May 01, 2020",
            Gender: "Female",
            "Flyer Program": "7th Heaven rewards    |   WE223546"
          }
        },
        {
          name: "Aubrey Mckinney",
          email: "kathrynpena@ibm.com",
          tel: "+380 66 255 33 67",
          messengersLogos: {
            whatsappDisabled: require("../../assets/whatsapp-disabled.svg"),
            telegram: require("../../assets/telegram.svg")
          },
          info: {
            "Passport Number": "FJ714612",
            "Passport Country": "Ukraine",
            "Passport Expiration": "May 01, 2020",
            Nationality: "Ukraine",
            "Date of Birth": "May 01, 2020",
            Gender: "Female",
            "Flyer Program": "7th Heaven rewards    |   WE223546"
          }
        },
        {
          name: "Greg Alexander",
          email: "kathrynpena@ibm.com",
          tel: "+380 66 255 33 67",
          messengersLogos: {
            whatsapp: require("../../assets/whatsapp.svg"),
            telegramDisabled: require("../../assets/telegram-disabled.svg")
          },
          info: {
            "Passport Number": "FJ714612",
            "Passport Country": "Ukraine",
            "Passport Expiration": "May 01, 2020",
            Nationality: "Ukraine",
            "Date of Birth": "May 01, 2020",
            Gender: "Female",
            "Flyer Program": "7th Heaven rewards    |   WE223546"
          }
        }
      ]
    };
  }
};
</script>

<style scoped lang="scss">
.guests-card {
  font-size: 14px;
  .custom-card-title {
    padding-top: 2px;
    font-size: 14px;
    font-family: CircularStd-Medium;
    color: rgba(41, 41, 73, 1);
  }
  .custom-divider {
    width: 710px;
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