<template>
  <div class="container">
    <VuePannellum
      src="https://pannellum.org/images/tocopilla.jpg"
      preview="https://pannellum.org/images/tocopilla-preview.jpg"
      :hot-spots="hotSpots"
      show-fullscreen
      auto-rotate
      compass
      :yaw="100"
      style="width: 600px; height: 400px;"
    />
    <VuePannellum
      :default="{
        firstScene: 'circle',
        author: 'Matthew Petroff',
        sceneFadeDuration: 1000,
      }"
      :scenes="scenes"
      auto-load
      show-fullscreen
      auto-rotate
      compass
      style="width: 600px; height: 400px;"
    />
  </div>
</template>
<!--src="https://pannellum.org/images/tocopilla.jpg"-->

<script>
export default {
  computed: {
    hotSpots() {
      return [
        {
          pitch: 0,
          yaw: -30,
          type: 'info',
          text: 'Baltimore Museum of Art',
          URL: 'https://cgworks.jp/',
        },
        {
          pitch: -0.4,
          yaw: 282.6,
          type: 'info',
          text: 'Art Museum Drive',
        },
        {
          pitch: -0.44,
          yaw: 123,
          type: 'info',
          text: 'North Charles Street',
        },
      ]
    },
    scenes() {
      return {
        circle: {
          title: 'Mason Circle',
          hfov: 110,
          pitch: -3,
          yaw: 117,
          type: 'equirectangular',
          panorama: 'https://pannellum.org/images/from-tree.jpg',
          hotSpots: [
            {
              pitch: -2.1,
              yaw: 132.9,
              type: 'scene',
              text: 'Spring House or Dairy',
              sceneId: 'house',
            },
          ],
        },

        house: {
          title: 'Spring House or Dairy',
          hfov: 110,
          yaw: 5,
          type: 'equirectangular',
          panorama: 'https://pannellum.org/images/bma-0.jpg',
          hotSpots: [
            {
              pitch: -0.6,
              yaw: 37.1,
              type: 'scene',
              text: 'Mason Circle',
              sceneId: 'circle',
              targetYaw: -23,
              targetPitch: 2,
            },
          ],
        },
      }
    },
  },
}
</script>

<style>
.container {
  display: flex;
  align-items: center;
  justify-content: space-around;
}
</style>
