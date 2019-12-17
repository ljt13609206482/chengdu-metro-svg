<style lang="stylus">
#line {
  path {
    stroke-width: 5px;
    stroke-linecap: round;
    fill: none;
    transition: 0.3s;

    &.is-show {
      opacity: 1;
    }
  }
}
</style>
<template>
  <g id="line" transform="translate(10 54)">
    <template v-for="item in data">
      <g
        :id="item.id"
        :key="item.id"
        :transform="`translate(${item.x || 0} ${item.y || 0})`"
        v-if="item.paths"
      >
        <path
          v-for="path in item.paths"
          :d="path.d"
          :key="path.id"
          :stroke="path.color"
          :transform="`translate(${path.x || 0} ${path.y || 0})`"
        ></path>
      </g>
      <path
        v-else
        :id="item.id"
        :key="item.id"
        :transform="`translate(${item.x || 0} ${item.y || 0})`"
        :d="item.d"
        :stroke="item.color"
      ></path>
    </template>
    <!-- <polyline :class="{'is-show': item.show}" :stroke="item.color" :id="item.id" :points="item.points" ></polyline> -->
  </g>
</template>

<script>
export default {
  components: {},

  props: {
    width: {
      type: Number
    },
    height: {
      type: Number
    },
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
