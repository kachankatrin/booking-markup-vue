<template>
  <v-timeline-item color="white" class="pb-0 custom-timeline-item" :class="lastClass" small>
    <v-row class="pt-1">
      <v-col cols="2" class="time-timetable">
        <ul class="d-flex">
          <li v-for="(value, name) in time" :key="name" class="time-timetable" :class="name">
            <strong
              v-if="name=== 'time'"
              class="time larger-font"
              style="color: rgba(41,41,73,1)"
            >{{value}}</strong>
            <strong v-else>{{value}}</strong>
          </li>
        </ul>
      </v-col>
      <v-col class="py-0">
        <ul>
          <li v-for="(value, name) in airport" :key="name">
            <div class="d-flex">
              <strong class="larger-font mr-3" style="color: rgba(41,41,73,1)">{{name}}</strong>
              <p style="font-family: Roboto" class="mb-2">{{value}}</p>
            </div>
            <div class="caption" style="font-family: Roboto; color: rgba(41,41,73,1)">{{city}}</div>
          </li>
        </ul>
      </v-col>
    </v-row>
  </v-timeline-item>
</template>
<script>
export default {
  name: "TimeLineEl",
  props: {
    time: {
      type: Object,
      required: true
    },
    airport: {
      type: Object,
      required: true
    },
    city: {
      type: String,
      required: true
    },
    lastClass: {
      type: String,
      required: false
    }
  }
};
</script>

<style lang="scss">
.custom-timeline-item {
  &.item-last {
    .v-timeline-item__body {
      padding-top: 15px;
      margin-bottom: 0px;
    }
    .v-timeline-item__divider {
      align-self: flex-end;
    }
  }
  .v-timeline-item__divider {
    .v-timeline-item__dot {
      &.v-timeline-item__dot--small {
        background: #C6CAD9;
        height: 9px;
        width: 9px;
        .v-timeline-item__inner-dot {
          &.white {
            height: 7px;
            width: 7px;
            margin: 1px;
          }
        }
      }
    }
  }
  .theme--light.v-timeline::before {
    background: rgba(198, 202, 217, 1);
  }
}
.list-cont {
  position: relative;
  .dotted-divider {
    border: solid 1px #7b819a;
    border-radius: 50%;
    width: 2px;
    height: 2px;
    position: absolute;
    left: -12%;
    &.flight {
      display: none;
    }
  }
}
</style>

<style lang="scss" scoped>
.larger-font {
  font-size: 14px;
}
.time-timetable {
  height: min-content;
  &.difference {
    margin-top: -5px;
  }
}
</style>