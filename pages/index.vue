<template>
  <body>
    <div>
      <Weather />
    </div>
  </body>
</template>

<script setup>
useSeoMeta({
  title: "WeatherApp",
  ogTitle: "WeatherApp",
  description: "Check the weather everywhere from anywhere.",
  ogDescription: "Check the weather everywhere from anywhere.",
  ogImage: "https://example.com/image.png",
  twitterCard: "summary_large_image",
});

useHead({
  script: [
    {
      src: "https://kit.fontawesome.com/f159836119.js",
      crossorigin: "anonymous",
      tagPosition: "bodyClose",
    },
  ],
});
</script>

<style scoped>
body {
  background-color: #121212 !important;
  font-family: "Roboto", Helvetica, Arial, sans-serif;
}
</style>
