<template>
  <div style="width: 100%; height: 100%;">
    <map
      id="map"
      scale="14"
      :markers="markers"
      show-location
      style="width: 100%; height: 100%;"
    ></map>
  </div>
</template>

<script>
export default {
  data () {
    return {
      markers: [{
        id: 0,
        latitude: 23.099994,
        longtitude: 113.324520,
        width: 50,
        height: 50
      }]
    }
  },
  methods: {
    markertap(event) {
      console.log(event)
    },
    controltap(event) {
      if (event.mp.controlId == 1) {
        this.scale += 1
      } if (event.mp.controlId == 2) {
        this.scale -= 1
      } else {
        this.markers = require("@/data/" + this.type + ".json").map((value) => {
          value.label = {}
          value.label.content = value.name
          value.label.color = '#FF7F00'
          value.label.fontSize = 14
          console.log(value)
          return value
        })
        this.type = this.type + 1;
        if (this.type == 6) this.type = 1
      }
    }
  },
  created () {
  }
}
</script>

<style>
body, html {
  height:100%
}
</style>