<template>
  <div class="pt-4">
    <ul class="d-flex justify-space-around">
      <li class="d-flex">
        <avatar-title
          :condition="true"
          style="color: #7B819A; font-family: Roboto !important; font-size: 13px !important; padding-left: 16px"
          :avatarTitle="letteredAvatar[guest.name]"
          :margins="'mr-4'"
          :value="guest.name"
          :color="colors[guest.name].avatar"
          :avatarSize="27"
        />
        <div style="position: relative">
          <v-icon
            small
            dark
            text-color="red"
            :color="colors[guest.name].icon"
            style="z-index: 9; top: 13px; left: 6px;"
          >{{icon}}</v-icon>
          <i class="icon-bg" :style="{background: colors[guest.name].bg}"></i>
        </div>
      </li>
      <li
        class="my-3 subtitle-1 card-subtitle pl-4"
        style="color: #7B819A; font-family: Roboto !important; font-size: 13px !important;"
      >{{guest.email}}</li>
      <div class="d-flex">
        <li
          class="my-3 subtitle-1 card-subtitle pl-4 mr-5"
          style="color: #7B819A; font-family: Roboto !important; font-size: 13px !important;"
        >{{guest.tel}}</li>
        <ul class="d-flex align-center justify-space-between" style="width: 44px">
          <li v-for="(value, name) in guest.messengersLogos" :key="name">
            <img :src="value" />
          </li>
        </ul>
      </div>
    </ul>
    <ul class="grid-container-guests pl-11 mb-6">
      <v-card-text
        class="card-text px-2"
        v-for="(value, name) in guest.info"
        :key="name"
        :class="name.includes('Flyer') ? 'flyer' : name"
      >
        <span>{{name}}:</span>
        <span style="color: rgb(123, 129, 154);">{{value}}</span>
      </v-card-text>
    </ul>
  </div>
</template>
<script>
import AvatarTitle from "../AvatarTitle";
export default {
  name: "SingleGuest",
  components: {
    AvatarTitle
  },
  props: {
    guest: {
      type: Object,
      required: true
    },
    icon: {
      type: String,
      required: false
    }
  },
  data() {
    return {
      colors: {
        "Mrs. Kathryn Pena": {
          avatar: "rgba(249,104,120,1)",
          bg: "rgba(250,180,63,1)",
          icon: "#FEE9C5"
        },
        "Aubrey Mckinney": {
          avatar: "rgba(242,201,76,1)",
          bg: "rgba(172,178,200,1)",
          icon: "rgba(235, 238, 244, 1)"
        },
        "Greg Alexander": {
          avatar: "rgba(106,78,255,1)",
          bg: "rgba(172,178,200,1)",
          icon: "rgba(235, 238, 244, 1)"
        }
      }
    };
  },
  computed: {
    letteredAvatar() {
      const avatarsObj = {};
      const namesArray = this.guest.name.split(" ");
      if (namesArray.indexOf("Mrs.") === -1) {
        namesArray;
      } else {
        namesArray.shift("Mrs.");
      }
      const singleLetterArr = namesArray.map(name => name.charAt(0));
      avatarsObj[this.guest.name] = singleLetterArr.join("");
      return avatarsObj;
    }
  }
};
</script>

<style lang="scss">
</style>

<style lang="scss" scoped>
.larger-font {
  font-size: 14px;
}
.grid-container-guests {
  display: grid;
  grid-template-rows: repeat(3, 40px);
  grid-template-columns: repeat(3, 1fr);
  max-height: 224px;
  width: 100%;
  &:nth-last-child(7) {
    grid-column: 1 / span 2;
  }
  .card-text {
    font-size: 12px;
    font-family: Roboto;
    &.flyer {
      grid-column: 1 / span 2;
    }
  }
}
.icon-bg {
  width: 12px;
  height: 12px;
  position: absolute;
  top: 20px;
  border-radius: 50%;
  left: 8px;
  z-index: 0;
}
</style>