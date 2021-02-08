<template>
  <v-card class="mx-8 my-7 px-5 py-6 luggage-card" max-width="420">
    <v-card-title class="d-flex justify-space-between custom-card-title">Luggage</v-card-title>
    <v-divider class="custom-divider"></v-divider>
    <v-card-text class="card-text">
      <ul>
        <li v-for="passanger in luggageCard.passangers" :key="passanger.name">
          <div
            class="my0 subtitle-1 card-subtitle"
            style="font-family: CircularStd-Book !important; font-size: 9px !important"
          >
            <avatar-title
              :avatarTitle="letteredAvatar[passanger.name]"
              :value="passanger.name"
              :color="colors[passanger.name]"
              :margins="'mr-2'"
              :condition="true"
              :avatarSize="20"
            />
          </div>
          <ul>
            <li
              v-for="luggage in passanger.baggage"
              :key="luggage.luggage"
              class="d-flex justify-space-between my-5 px-8 luggage-info"
            >
              <luggage-info :info="luggage.flight" />
              <luggage-info :info="luggage.luggage" />
              <luggage-info :info="luggage.price" />
            </li>
          </ul>
        </li>
      </ul>
    </v-card-text>
  </v-card>
</template>

<script>
import LuggageInfo from "./LuggageInfo.vue";
import AvatarTitle from "./AvatarTitle.vue";
export default {
  name: "LuggageCard",
  components: { AvatarTitle, LuggageInfo },
  data() {
    return {
      colors: {
        "Kathryn Pena": "rgba(249,104,120,1)",
        "Lee Nguyen": "rgba(160,196,247,1)"
      },
      luggageCard: {
        passangers: [
          {
            name: "Kathryn Pena",
            baggage: [
              {
                flight: "JFK - FRA",
                luggage: "1 x 15kg checked bag",
                price: "$14"
              },
              {
                flight: "JFK - FRA",
                luggage: "1 x 15kg checked bag",
                price: "$14"
              }
            ]
          },
          {
            name: "Lee Nguyen",
            baggage: [
              {
                flight: "JFK - FRA",
                luggage: "1 x 15kg checked bag",
                price: "$14"
              },
              {
                flight: "JFK - FRA",
                luggage: "1 x 15kg checked bag",
                price: "$14"
              }
            ]
          }
        ]
      }
    };
  },
  computed: {
    letteredAvatar() {
      const avatarsObj = {};
      this.luggageCard.passangers.map(passanger => {
        for (const pass in passanger) {
          if (pass === "name") {
            const value = passanger[pass];
            const namesArray = value.split(" ");
            const singleLetterArr = namesArray.map(name => name.charAt(0));
            avatarsObj[value] = singleLetterArr.join("");
          }
        }
      });
      return avatarsObj;
    }
  }
};
</script>

<style scoped lang="scss">
.luggage-card {
  font-size: 12px;
  .custom-card-title {
    padding-top: 2px;
    font-size: 14px;
    font-family: CircularStd-Medium;
    color: rgba(41,41,73,1);
  }
  .custom-divider {
    width: 420px;
    margin-left: -20px;
    max-width: unset;
  }
  .card-text {
    padding-bottom: 0;
    .luggage-info {
      background: rgba(245, 248, 254, 1);
      border-radius: 4px;
    }
  }
}
.v-application {
  ul {
    padding-left: 0;
  }
}
</style>