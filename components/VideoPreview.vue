<template>
  <div style = "width: 280px; height : 100px">

    <nuxt-link :to="redirectPage">
      <b-image
        class='anime_image'
        :src="url"
        :webp-fallback="url"
        ratio="0.5by0.5"
        rounded
      ></b-image>
      <div class="box anime_title rounded-3xl">
        <span class='main_title'>&nbsp;{{ title }}</span>
        <span class='sub_title'>&nbsp;{{ timeCode }}</span>
      </div>
    </nuxt-link>

  </div>
</template>

<script>
export default {
  name: "VideoPreview",
  props: ['url', 'title', 'timeCode', 'redirectPage']
}
</script>

<style scoped>

.anime_image {
  width: 80px;
  height: 80px;
  z-index: 1;
}

.anime_title {
  position: relative;
  bottom: 75px;
  left: 65px;
  width: 220px;
  height: 70px;
  background: #2c2c2c;
  z-index: 0;
}

.main_title {
  position: absolute;
  top: 10px;
  color: #cdcdd4;
}

.sub_title {
  position: relative;
  top: 10px;
  color: #9c9ca6;
}

</style>
