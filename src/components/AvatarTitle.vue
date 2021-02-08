<template>
  <div class="d-flex align-center">
    <v-avatar class="my-3 mr-2" :class="margins" :color="color" :size="avatarSize" v-if="condition">
      <span class="white--text avatar-text">{{avatarTitle}}</span>
    </v-avatar>
    <div
      v-if="name === 'Status:'"
      class="my-3 subtitle-1 card-subtitle"
      style="font-family: CircularStd-Book !important; font-size: 12px !important"
    >
      <v-chip
        class="custom-chip"
        color="rgb(97, 219, 180, 0.2)"
        style="font-family: CircularStd-Medium;"
        small
        text-color="#4DC7A0"
      >
        <v-icon left small>mdi-check-bold</v-icon>
        {{value}}
      </v-chip>
    </div>
    <div
      v-else
      class="my-3 subtitle-1 card-subtitle"
      style="font-family: CircularStd-Book !important; font-size: 12px !important"
    >{{value}}</div>
  </div>
</template>

<script>
export default {
  name: "AvatarTitle",
  props: {
    avatarTitle: {
      type: String,
      required: false
    },
    color: {
      type: String,
      required: false
    },
    value: {
      type: String,
      required: false
    },
    name: {
      type: String,
      required: false
    },
    condition: {
      type: Boolean,
      required: true
    },
    margins: {
      type: String,
      required: false
    },
    avatarSize: {
      type: String,
      required: false
    }
  }
};
</script>

<style lang="scss" scoped>
.avatar-text {
  font-size: inherit;
  font-family: Roboto;
  font-weight: 500;
  padding-left: 1px;
}
</style>