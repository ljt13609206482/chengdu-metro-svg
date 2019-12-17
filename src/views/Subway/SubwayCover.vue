<style lang="stylus">
.dot-style{
  fill:url(#grad1);
  cursor:pointer;
  position:relative;
}
</style>
<template>
  <g>
    <g
      id="station-cover"
      transform="translate(-40 53)"
      v-if="data.stations.length > 0"
    >
      <g
        v-if="item.coverX && item.coverY"
        v-for="(item, index) in stations"
        :key="index"
        :data-name="item.name"
        :transform="`translate(${item.coverX} ${item.coverY})`"
      >
        <defs>
          <radialGradient
            id="grad1"
            cx="50%"
            cy="50%"
            r="50%"
            fx="50%"
            fy="50%"
          >
            <stop offset="0%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
            <stop
              offset="70%"
              style="stop-color:rgb(255,0,0);stop-opacity:0.8"
            />
            <stop
              offset="100%"
              style="stop-color:rgb(255,255,255);stop-opacity:1"
            />
          </radialGradient>
        </defs>
        <template>
          <circle
            v-if="item.status < 5000 && item.status > 0"
            class="dot-style"
            cx="10"
            cy="10"
            r="10"
            @mouseenter="show(item, $event)"
            @mouseleave="leave"
          >
            <animate
              id="ani1"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="0s;ani2.end"
              dur="1s"
              from="1"
              to="0.4"
              fill="freeze"
            />
            <animate
              id="ani2"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="ani1.end"
              dur="1s"
              from="0.4"
              to="1"
              fill="freeze"
            />
          </circle>
          <circle
            v-if="item.status < 10000 && item.status > 5000"
            class="dot-style"
            cx="15"
            cy="15"
            r="15"
            @mouseenter="show(item, $event)"
            @mouseleave="leave"
          >
            <animate
              id="ani1"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="0s;ani2.end"
              dur="1s"
              from="1"
              to="0.4"
              fill="freeze"
            />
            <animate
              id="ani2"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="ani1.end"
              dur="1s"
              from="0.4"
              to="1"
              fill="freeze"
            />
          </circle>
          <circle
            v-if="item.status < 20000 && item.status > 10000"
            class="dot-style"
            cx="20"
            cy="20"
            r="20"
            @mouseenter="show(item, $event)"
            @mouseleave="leave"
          >
            <animate
              id="ani1"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="0s;ani2.end"
              dur="1s"
              from="1"
              to="0.4"
              fill="freeze"
            />
            <animate
              id="ani2"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="ani1.end"
              dur="1s"
              from="0.4"
              to="1"
              fill="freeze"
            />
          </circle>
          <circle
            v-if="item.status > 20000"
            class="dot-style"
            cx="25"
            cy="25"
            r="25"
            @mouseenter="show(item, $event)"
            @mouseleave="leave"
          >
            <animate
              id="ani1"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="0s;ani2.end"
              dur="1s"
              from="1"
              to="0.4"
              fill="freeze"
            />
            <animate
              id="ani2"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="ani1.end"
              dur="1s"
              from="0.4"
              to="1"
              fill="freeze"
            />
          </circle>
        </template>
      </g>
    </g>
    <g
      id="station-ex-cover"
      transform="translate(2)"
      v-if="data.stationExs.length > 0"
    >
      <g
        v-if="item.coverX && item.coverY"
        v-for="(item, index) in stationExs"
        :key="index"
        :data-name="item.name"
        :transform="`translate(${item.coverX} ${item.coverY})`"
      >
        <defs>
          <radialGradient
            id="grad1"
            cx="50%"
            cy="50%"
            r="50%"
            fx="50%"
            fy="50%"
          >
            <stop offset="0%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
            <stop
              offset="70%"
              style="stop-color:rgb(255,0,0);stop-opacity:0.8"
            />
            <stop
              offset="100%"
              style="stop-color:rgb(255,255,255);stop-opacity:1"
            />
          </radialGradient>
        </defs>
        <template>
          <circle
            v-if="item.status < 5000 && item.status > 0"
            class="dot-style"
            cx="10"
            cy="10"
            r="10"
            @mouseenter="show(item, $event)"
            @mouseleave="leave"
          >
            <animate
              id="ani1"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="0s;ani2.end"
              dur="1s"
              from="1"
              to="0.4"
              fill="freeze"
            />
            <animate
              id="ani2"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="ani1.end"
              dur="1s"
              from="0.4"
              to="1"
              fill="freeze"
            />
          </circle>
          <circle
            v-if="item.status < 10000 && item.status > 5000"
            class="dot-style"
            cx="15"
            cy="15"
            r="15"
            @mouseenter="show(item, $event)"
            @mouseleave="leave"
          >
            <animate
              id="ani1"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="0s;ani2.end"
              dur="1s"
              from="1"
              to="0.4"
              fill="freeze"
            />
            <animate
              id="ani2"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="ani1.end"
              dur="1s"
              from="0.4"
              to="1"
              fill="freeze"
            />
          </circle>
          <circle
            v-if="item.status < 20000 && item.status > 10000"
            class="dot-style"
            cx="20"
            cy="20"
            r="20"
            @mouseenter="show(item, $event)"
            @mouseleave="leave"
          >
            <animate
              id="ani1"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="0s;ani2.end"
              dur="1s"
              from="1"
              to="0.4"
              fill="freeze"
            />
            <animate
              id="ani2"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="ani1.end"
              dur="1s"
              from="0.4"
              to="1"
              fill="freeze"
            />
          </circle>
          <circle
            v-if="item.status > 20000"
            class="dot-style"
            cx="25"
            cy="25"
            r="25"
            @mouseenter="show(item, $event)"
            @mouseleave="leave"
          >
            <animate
              id="ani1"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="0s;ani2.end"
              dur="1s"
              from="1"
              to="0.4"
              fill="freeze"
            />
            <animate
              id="ani2"
              attributeName="fill-opacity"
              attributeType="XML"
              begin="ani1.end"
              dur="1s"
              from="0.4"
              to="1"
              fill="freeze"
            />
          </circle>
        </template>
      </g>
    </g>
  </g>
</template>

<script>
export default {
  components: {},
  props: {
    data: Object
  },

  data() {
    return {};
  },

  computed: {
    stations() {
      const stations = this.data.stations;
      stations.map(item => {
        item.x = item.x || 0;
        item.y = item.y || 0;
        if (item.status < 5000 && item.status > 0) {
          item.coverX = item.x - 4;
          item.coverY = item.y - 4;
        }
        if (item.status < 10000 && item.status > 5000) {
          item.coverX = item.x - 10;
          item.coverY = item.y - 10;
        }
        if (item.status < 20000 && item.status > 10000) {
          item.coverX = item.x - 15;
          item.coverY = item.y - 15;
        }
        if (item.status > 20000) {
          item.coverX = item.x - 17.5;
          item.coverY = item.y - 20;
        }
      });
      return stations;
    },
    stationExs() {
      const stations = this.data.stationExs;
      stations.map(item => {
        item.x = item.x || 0;
        item.y = item.y || 0;
        if (item.status < 5000 && item.status > 0) {
          item.coverX = item.x + 2;
          item.coverY = item.y - 3;
        }
        if (item.status < 10000 && item.status > 5000) {
          item.coverX = item.x - 4;
          item.coverY = item.y - 10;
        }
        if (item.status < 20000 && item.status > 10000) {
          item.coverX = item.x - 10;
          item.coverY = item.y - 15;
        }
        if (item.status > 20000) {
          item.coverX = item.x - 12.5;
          item.coverY = item.y - 20;
        }
      });
      return stations;
    }
  },
  watch: {
    data: {
      handler(newValue, oldValue) {
        this.$nextTick(() => {
          this.data = newValue;
        });
      },
      deep: true
    }
  },
  mounted() {},

  methods: {
    show(item, event) {
      this.$emit("hoverHandle", item, event);
    },
    leave() {
      this.$emit("leaveHandle");
    }
  }
};
</script>
