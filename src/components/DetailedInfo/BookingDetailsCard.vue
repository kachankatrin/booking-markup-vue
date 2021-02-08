<template>
  <v-card class="mx-auto my-7 px-5 pt-6 booking-details-card" max-width="710">
    <v-card-title class="d-flex justify-space-between custom-card-title">Booking Details</v-card-title>
    <v-divider class="custom-divider"></v-divider>
      <v-card-text class="card-text">
        <ul class>
          <li v-for="ticket in tickets" :key="ticket.carrier" class="py-10 ticket-single">
            <div class="d-flex justify-space-between mb-8">
              <div class="d-flex">
                <img :src="ticket.logo" alt="logo" class="align-self-baseline mr-7" />
                <div class="d-flex flex-column">
                  <p class="mb-3">{{ticket.carrier}}</p>
                  <ul class="d-flex justify-space-between flight-details">
                    <li
                      v-for="(value, name) in ticket.flightDetails"
                      :key="name"
                      class="d-flex align-center list-cont"
                    >
                      <hr class="dotted-divider" :class="name" />
                      {{value}}
                    </li>
                  </ul>
                </div>
              </div>
              <v-chip
                class="mb-0 custom-chip"
                color="rgba(243,245,248,0.8)"
                label
                small
                text-color="#7b819a"
              >{{ticket.dateOfFlight}}</v-chip>
            </div>
            <div class="d-flex justify-space-between">
              <v-container>
                <v-timeline align-top dense class="pt-0">
                  <time-line-el
                    :time="ticket.timeline.depature.time"
                    :airport="ticket.timeline.depature.airport"
                    :city="ticket.timeline.depature.city"
                  />
                  <v-timeline-item class="pb-0 custom-timeline-item" hide-dot>
                    <v-row class="pt-8">
                      <v-col cols="2">
                        <p class="duration">Duration</p>
                      </v-col>
                      <v-col>
                        <p class="duration duration-time">
                          <v-icon
                            x-small
                            color="#7B819A"
                            style="left: -8px; vertical-align: initial"
                          >mdi-clock-time-four-outline</v-icon>
                          {{ticket.timeline.duration}}
                        </p>
                      </v-col>
                    </v-row>
                  </v-timeline-item>
                  <time-line-el
                    :time="ticket.timeline.arrival.time"
                    :airport="ticket.timeline.arrival.airport"
                    :city="ticket.timeline.arrival.city"
                    :lastClass="'item-last'"
                  />
                </v-timeline>
              </v-container>
              <ul class="mt-4">
                <li v-for="(value, name) in ticket.refunds" :key="name" class="d-flex" style="color: rgba(123,129,154,1); font-family: Roboto">
                    <v-icon small color="#B0B3C2">{{value[0]}}</v-icon>
                    <a href="#" style="color: rgba(123,129,154,1);" class="mx-3">{{name}}</a>
                    <v-icon v-if="value[1]" color="#B0B3C2" small>{{value[1]}}</v-icon>
                    </li>
              </ul>
            </div>
          </li>
        </ul>
      </v-card-text>
  </v-card>
</template>

<script>
import TimeLineEl from "./TimeLineEl";
export default {
  name: "BookingDetailsCard",
  components: { TimeLineEl },
  data() {
    return {
      tickets: [
        {
          carrier: "Delta Air Lines",
          logo: require("../../assets/delta-logo.svg"),
          flightDetails: {
            flight: "DL9367",
            class: "Economy",
            plane: "Airbus A330-200"
          },
          dateOfFlight: "Tue, April 25, 2020",
          timeline: {
            depature: {
              time: { time: "19:55" },
              airport: { JFK: "John F. Kennedy International" },
              city: "New York"
            },
            duration: "7h 55m",
            arrival: {
              time: { time: "09:50", difference: "+1" },
              airport: { FRA: "Frankfurt International Airport" },
              city: "Frankfurt"
            }
          },
          refunds: {
            Refundable: ["mdi-repeat", "mdi-arrange-bring-forward"],
            "Fare rules": ["mdi-database-outline"]
          }
        },
        {
          carrier: "KLM Royal Dutch Airlines (operated by Delta Air Lines)",
          logo: require("../../assets/klm-logo.svg"),
          flightDetails: {
            flight: "DL9367",
            class: "Economy",
            plane: "Airbus A330-200"
          },
          dateOfFlight: "Fr, May 01, 2020",
          timeline: {
            depature: {
              time: { time: "19:55" },
              airport: { FRA: "Frankfurt International Airport" },
              city: "Frankfurt"
            },
            duration: "7h 55m",
            arrival: {
              time: { time: "09:50", difference: "+1" },
              airport: { JFK: "John F. Kennedy International" },
              city: "New York"
            }
          },
          refunds: {
            Refundable: ["mdi-repeat", "mdi-arrange-bring-forward"],
            "Fare rules": ["mdi-database-outline"]
          }
        }
      ]
    };
  }
};
</script>


<style lang="scss" scoped>

.booking-details-card {
  font-size: 14px;
  font-family: CircularStd-Medium;
  .custom-card-title {
    padding-top: 2px;
    font-size: 14px;
    font-family: CircularStd-Medium;
    color: rgba(41, 41, 73, 1);
  }
}
.v-timeline {
  &:before {
    height: calc(100% - 24px);
    position: absolute;
    top: 8%;
  }
}
.custom-divider {
  width: 710px;
  margin-left: -20px;
  max-width: unset;
}
.card-text {
  color: #7b819a;
  font-size: 12px;
  .flight-details {
    width: 222px;
  }
}
.duration {
  font-family: Roboto;
  &.duration-time {
    font-family: Roboto;
    margin-left: -3px;
  }
}
</style>
<style >
.v-application--wrap {
  min-height: unset;
}
.ticket-single {
    opacity: 0.7;
    border-bottom: 1px dashed #D4DBE7;
    box-sizing: border-box;
}
.ticket-single:nth-of-type(2) {
  border: none
}
</style>