<template>
  <div
    class="my0 subtitle-1 card-subtitle"
    style="font-family: Roboto !important; font-size: 12px !important"
  >{{info}}</div>
</template>

<script>
export default {
  name: "LuggageInfo",
  props: {
    info: {
      type: String,
      required: true
    }
  }
};
</script>