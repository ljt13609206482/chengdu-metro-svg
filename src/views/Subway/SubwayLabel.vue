<style lang="stylus">
#text {
  fill: #050000;
  font-size: 10px;
  font-family: STSong;
  transition: 0.3;

  &.is-show {
    opacity: 1;
  }
}
</style>
<template>
  <g id="text" transform="translate(2 -1)">
    <text
      class="subway-label"
      :class="{ 'is-show': item.show }"
      :transform="`translate(${item.x || 0} ${item.y || 0})`"
      :data-name="item.title"
      v-for="(item, index) in data"
      :key="index"
    >
      <tspan
        :x="tspan.x"
        :y="tspan.y"
        :key="tspan.name"
        v-for="tspan in item.tspan"
        >{{ tspan.name }}</tspan
      >
    </text>
  </g>
</template>

<script>
export default {
  components: {},

  props: {
    data: Array
  },

  data() {
    return {};
  },

  computed: {},

  mounted() {},

  methods: {}
};
</script>
