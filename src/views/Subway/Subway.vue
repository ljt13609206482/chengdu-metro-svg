<style lang="stylus">
.subway {
  position: relative;
  width:150%;
  height: 100%;
  overflow: hidden;
  top:0;
  left :-25%;

  >.svg-box {
    position: absolute;
    -webkit-user-select: none;
	-moz-user-select: none;
	-ms-user-select: none;
	user-select: none;
  -webkit-user-drag: none;


  .tooltip-box{
      padding:10px;
      z-index :999;
      background :rgba(0,0,0,0.6);
      border-radius:5px;
      color :#fff;
      position:absolute;
      left :0;
      top:0;
      box-sizing :border-box;
    }
  }

  svg {
    position: absolute;
    left:0;
    top:0;
    -webkit-user-select: none;
	-moz-user-select: none;
	-ms-user-select: none;
	user-select: none;
  -webkit-user-drag: none;
  }

  .subway-stations {
    z-index: 20;
  }

  .subway-line {
    z-index: 10;
  }

  .subway-label {
    z-index: 30;
  }

  .subway-bg {
    z-index: -1;
  }
}
</style>
<template>
  <div class="subway" id="subway-box">
    <div
      class="svg-box"
      id="svg-box"
      :style="
        'width:' +
          boxWidth +
          '%;top:' +
          topPosition +
          '%;left:' +
          leftPosition +
          '%'
      "
      @mousedown="draggableFun($event)"
    >
      <div
        class="tooltip-box"
        :style="'left:' + left + 'px;top:' + top + 'px;'"
        v-show="tipText != ''"
      >
        <div class="text-box">
          <p>{{ tipText }}</p>
          <p>数量:{{ tipValue }}</p>
        </div>
      </div>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        :viewBox="`0 0 ${viewBox.width || 0} ${viewBox.height || 0}`"
      >
        <g id="cdmetro" transform="translate(541 219)">
          <subway-line :data="lines"></subway-line>
          <subway-station :data="stations"></subway-station>
          <subway-ex-station :data="stationExs"></subway-ex-station>
          <subway-label :data="texts"></subway-label>
          <subway-introduce></subway-introduce>
          <subway-cover
            :data="allStations"
            @hoverHandle="hoverMethod"
            @leaveHandle="mousrOutHandle"
          ></subway-cover>
        </g>
      </svg>
    </div>
  </div>
</template>

<script>
import SubwayIntroduce from "./SubwayIntroduce";
import SubwayLine from "./SubwayLine";
import SubwayStation from "./SubwayStation";
import SubwayExStation from "./SubwayExStation";
import SubwayLabel from "./SubwayLabel";
import SubwayCover from "./SubwayCover";
export default {
  components: {
    SubwayIntroduce,
    SubwayLine,
    SubwayStation,
    SubwayExStation,
    SubwayLabel,
    SubwayCover
  },
  data() {
    return {
      boxWidth: "100",
      topPosition: "-0",
      leftPosition: "-0",
      tipText: "",
      tipValue: "",
      left: "",
      top: "",
      eleWidth: "",
      eleHeight: ""
    };
  },
  props: {
    viewBox: Object,
    lines: Array,
    stations: Array,
    stationExs: Array,
    texts: Array,
    test: String
  },
  watch: {
    stations: {
      handler(newValue, oldValue) {
        this.stations = newValue;
      },
      deep: true
    },
    stationExs: {
      handler(newValue, oldValue) {
        this.stationExs = newValue;
      },
      deep: true
    }
  },
  computed: {
    allStations() {
      return { stations: this.stations, stationExs: this.stationExs };
    }
  },

  mounted() {},

  methods: {
    // 元素拖动方法
    draggableFun(val) {
      let _this = this;
      var div = document.getElementById("svg-box");
      var dragFlag = false;
      var x, y;

      div.onmousedown = function(e) {
        e = e || window.event;
        x = e.clientX - div.offsetLeft;
        y = e.clientY - div.offsetTop;
        dragFlag = true;
      };

      div.onmousemove = function(e) {
        if (dragFlag) {
          e = e || window.event;
          div.style.left = e.clientX - x + "px";
          div.style.top = e.clientY - y + "px";
        }
      };
      div.onmouseup = function(e) {
        dragFlag = false;
      };
      div.onmouseleave = function(e) {
        dragFlag = false;
      };
      var div2 = document.getElementById("subway-box");

      div2.onmousewheel = function(e1) {
        e1 = e1 || window.event;
        // console.log(e1)
        if (e1.deltaY) {
          // 判断浏览器IE，谷歌滑轮事件
          if (e1.deltaY > 0 && _this.boxWidth > 100) {
            // 当滑轮向上滚动时
            let boxWidth = new Number(_this.boxWidth);
            let leftPosition = new Number(_this.leftPosition);
            let topPosition = new Number(_this.topPosition);
            boxWidth -= 10;
            leftPosition += 5;
            topPosition += 5;
            _this.boxWidth = boxWidth.toString();
            _this.leftPosition = leftPosition.toString();
            _this.topPosition = topPosition.toString();
          }
          if (e1.deltaY < 0 && _this.boxWidth < 500) {
            // 当滑轮向下滚动时
            let boxWidth = new Number(_this.boxWidth);
            let leftPosition = new Number(_this.leftPosition);
            let topPosition = new Number(_this.topPosition);
            boxWidth += 10;
            leftPosition -= 5;
            topPosition -= 5;
            _this.boxWidth = boxWidth.toString();
            _this.leftPosition = leftPosition.toString();
            _this.topPosition = topPosition.toString();
          }
        }
      };
      div2.addEventListener("DOMMouseScroll", function(e1) {
        e1 = e1 || window.event;
        if (e1.detail) {
          // 判断浏览器firFox,鼠标滚动事件
          if (e1.detail > 0 && _this.boxWidth > 100) {
            // 当滑轮向上滚动时
            let boxWidth = new Number(_this.boxWidth);
            let leftPosition = new Number(_this.leftPosition);
            let topPosition = new Number(_this.topPosition);
            boxWidth -= 10;
            leftPosition += 5;
            topPosition += 5;
            _this.boxWidth = boxWidth.toString();
            _this.leftPosition = leftPosition.toString();
            _this.topPosition = topPosition.toString();
          }
          if (e1.detail < 0 && _this.boxWidth < 500) {
            // 当滑轮向下滚动时
            let boxWidth = new Number(_this.boxWidth);
            let leftPosition = new Number(_this.leftPosition);
            let topPosition = new Number(_this.topPosition);
            boxWidth += 10;
            leftPosition -= 5;
            topPosition -= 5;
            _this.boxWidth = boxWidth.toString();
            _this.leftPosition = leftPosition.toString();
            _this.topPosition = topPosition.toString();
          }
        }
      });
    },
    hoverMethod(item, event) {
      this.tipText = item.name;
      this.tipValue = item.status;
      this.left = event.offsetX;
      this.top = event.offsetY - 65;
    },
    mousrOutHandle() {
      this.tipText = "";
      this.tipValue = "";
    }
  }
};
</script>
