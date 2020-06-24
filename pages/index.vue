<template>
  <div class="container">
    <VuePannellum
      :hot-spots="hotSpots"
      src="https://pannellum.org/images/tocopilla.jpg"
      preview="https://pannellum.org/images/tocopilla-preview.jpg"
      show-fullscreen
      auto-rotate
      compass
      style="height: 100vh;"
    />
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
          pitch: -0.9,
          yaw: 124.4,
          type: 'info',
          text: 'North Charles Street',
        },
      ]
    },
  },
}
</script>

<style></style>
