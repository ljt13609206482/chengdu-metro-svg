<style lang="stylus">
#station {
  fill: #fff;
  stroke: #050000;
  cursor: pointer;
  transition: 0.3;

  &.is-show {
    opacity: 1;
  }

  &:hover {
    stroke: #000;
  }
}

#station .cls-10 {
  stroke: none;
}

#station .cls-1, #station .cls-11, #station .cls-2, #station .cls-3, #station .cls-4, #station .cls-5, #station .cls-6, #station .cls-7 {
  fill: none;
}

#station .cls-8 {
  fill: #fff;
  stroke: #050000;
}
</style>
<template>
  <g id="station" transform="translate(-40 53)">
    <g
      class="cls-8"
      v-for="(item, index) in data"
      :key="index"
      :data-name="item.name"
      :transform="`translate(${item.x || 0} ${item.y || 0})`"
    >
      <template>
        <circle class="cls-10" cx="6" cy="6" r="6" />
        <circle class="cls-11" cx="6" cy="6" r="5.5" />
      </template>
    </g>
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
