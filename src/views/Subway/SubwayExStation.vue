<style lang="stylus">
#station-ex {
  fill: #fff;
  stroke: #333;
  cursor: pointer;
  transition: 0.3;

  &.is-show {
    opacity: 1;
  }

  &:hover {
    stroke: #000;
  }
}
</style>
<template>
  <g id="station-ex" transform="translate(2)">
    <rect
      :data-name="item.name"
      class="cls-8"
      v-for="(item, index) in data"
      :key="index"
      :width="item.width"
      :height="item.height"
      rx="4.5"
      :transform="`translate(${item.x || 0} ${item.y || 0})`"
    />
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

  methods: {
    show(item) {
      console.log(item);
    }
  }
};
</script>
