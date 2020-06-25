<template>
  <div style="display: flex; justify-content: space-between; padding: 10px;">
    <div style="width: 30%;">
      <VuePannellum
        src="https://pannellum.org/images/tocopilla.jpg"
        preview="https://pannellum.org/images/tocopilla-preview.jpg"
        :hot-spots="hotSpots"
        show-fullscreen
        auto-rotate
        hot-spot-debug
        compass
        :yaw="100"
        style="width: 100%; height: 400px;"
        title="Using hot spots, auto-rotate"
      />
    </div>
    <div style="width: 30%;">
      <VuePannellum
        :default="{
          firstScene: 'circle',
          author: 'Matthew Petroff',
          sceneFadeDuration: 1000,
        }"
        :scenes="scenes"
        auto-load
        show-fullscreen
        style="width: 100%; height: 400px;"
        title="Using tours, auto-load"
        class="panellum1"
      />
    </div>
    <div style="width: 30%;">
      <VPannellum
        height="100%"
        :width="500"
        panorama="https://pannellum.org/images/lascar.jpg"
        auto-load
        :pitch="-10"
        :yaw="135.4"
        :hfov="100"
        compass
        style="z-index: 100;"
        title="Using new components, auto rotate inactivity delay"
      />
    </div>
  </div>
</template>

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
