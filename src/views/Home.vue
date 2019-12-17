<!--  -->
<template>
  <div class="main-section">
    <div class="svg-map-box">
      <subway :lines="lines" :view-box="viewBox" :stations="stations" :texts="texts" :station-exs="stationExs"
        test="test" />
    </div>
  </div>
</template>

<script>
import data from "../../public/data/cdmetro-subway";
import Subway from "./Subway/Subway";

export default {
  components: {
    Subway
  },
  data() {
    return {
      lines: [],
      viewBox: {},
      stations: [],
      stationExs: [],
      texts: []
    };
  },
  computed: {},
  mounted() {
    this.lines = data.lines;
    this.stations = data.stations;
    this.stationExs = data["station-ex"];
    this.texts = data.texts;
    this.viewBox = {
      width: data.width,
      height: data.height
    };
  },
  methods: {}
};
</script>
<style scoped>
  .main-section{
    width: 100%;
    height: 100%;
  }
  .svg-map-box{
  width: 100%;
  height: 100%;
  background: #ffffff;
  overflow: hidden;
}
</style>
