<template>
  <v-card class="mx-8 my-7 px-5 py-6 booking-card" max-width="420">
    <v-card-title class="d-flex justify-space-between custom-card-title">
      Booking Details
      <v-chip
        class="mb-0 custom-chip"
        color="#61DBB4"
        label
        small
        text-color="white"
      >{{bookingId.name}}:{{bookingId.id}}</v-chip>
    </v-card-title>
    <v-divider class="custom-divider"></v-divider>
    <v-card-text class="card-text">
      <ul>
        <li v-for="(value, name) in bookingCard" :key="name" class="d-flex justify-space-between" style="font-size: 9px;">
          <div
            v-if="name==='Member'"
            class="my-3 subtitle-1 card-subtitle"
            style="font-family: CircularStd-Book !important; font-size: 12px !important"
          >
            <v-chip
              class="mx-2 custom-chip"
              color="#F5F8FE"
              style="font-family: CircularStd-Book; color: #7B819A;"
              label
              small
              text-color="initial"
            >{{name}}</v-chip>
          </div>
          <div
            v-else
            class="my-3 subtitle-1 card-subtitle"
            style="font-family: CircularStd-Book !important; font-size: 12px !important"
          >{{name}}</div>
          <avatar-title
            :condition="name === 'Booked by:'"
            :margins="'mr-2'"
            :value="value"
            :name="name"
            :avatarTitle="letteredAvatar[value]"
            :color="'rgba(250,180,63,1)'"
            :avatarSize="20"
          />
        </li>
      </ul>
    </v-card-text>
  </v-card>
</template>

<script>
import AvatarTitle from "./AvatarTitle.vue";
export default {
  name: "BookingCardSmall",
  components: { AvatarTitle },
  data() {
    return {
      bookingId: { name: "Booking ID", id: "239503" },
      bookingCard: {
        "Booked by:": "Kirill Buriak",
        Member: "kathrynpena@ibm.com",
        "Booking date:": "May 1, 2020",
        "Status:": "Confirmed"
      },
    };
  },
  computed: {
    letteredAvatar() {
      const avatarsObj = {};
      for (const det in this.bookingCard) {
        const value = this.bookingCard[det];
        if (det === "Booked by:") {
          const namesArray = value.split(" ");
          const singleLetterArr = namesArray.map(name => name.charAt(0));
          avatarsObj[value] = singleLetterArr.join("");
        }
      }
      return avatarsObj;
    }
  },
};
</script>

<style scoped lang="scss">
.booking-card {
  font-size: 12px;
  .custom-card-title {
    padding-top: 2px;
    font-size: 14px;
    font-family: CircularStd-Medium;
    color: rgba(41, 41, 73, 1);
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