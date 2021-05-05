<template>
  <section>
    <div class="box secondary_back index-content"
         :style="{ 'max-width' : this.contentWidth }"><br>
      <div v-for="preview in previews" :key="preview.title" class="anime_item" :style="{ 'float' : previewFloatControl ? 'auto' : preview.float  }">
        <VideoPreview :url="preview.url" :title="preview.title" :redirect-page="preview.redirectPage"
                      :time-code="preview.timeCode"/>
      </div>
    </div>
  </section>
</template>

<style>

.secondary_back {
  background: #1f1f1f !important;
}

div.index-content {
  position: relative;
  bottom: 35px;
  z-index: 0;
  margin: auto;
}

.anime_item {
  width: 280px;
}
</style>

<script>

import VideoPreview from "@/components/VideoPreview";

export default {
  name: 'HomePage',
  data() {
    return {
      isSwitchedCustom: "Шакалить",
      isSwitched: false,
      loginEmail: "",
      pwd: "",
      contentWidth: "",
      anime_list: ['Моя геройская академия', 'Магическая битва', 'Атака Титанов', 'Тёмный дворецкий', 'Семь смертных грехов', 'Восхождение героя щита', 'Дневник будущего'].sort(),
      previews: {
        sevens: {
          url: "https://gen.jut.su/uploads/animethumbs/anime_nanatsu-no-taizai.jpg",
          title: "Семь смертных грехов",
          timeCode: "16 серия (4 сезон)",
          redirectPage: "/",
          float: "right"
        },
        magicFight: {
          url: "https://gen.jut.su/uploads/animethumbs/anime_jujutsu-kaisen.jpg",
          title: "Магическая битва",
          timeCode: "3 серия",
          redirectPage: "/",
          float: "auto"
        },
        onePunchMan: {
          url: "https://gen.jut.su/uploads/animethumbs/anime_one-punch-man.jpg",
          title: "Ванпанчмен",
          timeCode: "9 серия (2 сезон)",
          redirectPage: "/",
          float: "right"
        },
        heroShield: {
          url: "https://gen.jut.su/uploads/animethumbs/anime_tate-yuusha-nariagari.jpg",
          title: "Восхождение героя щита",
          timeCode: "14 серия",
          redirectPage: "/",
          float: "auto"
        },
        futureDiary: {
          url: "https://gen.jut.su/uploads/animethumbs/anime_mirai-nikki.jpg",
          title: "Дневник будущего",
          timeCode: "19 серия",
          redirectPage: "/",
          float: "right"
        },
        darkButler: {
          url: "https://gen.jut.su/uploads/animethumbs/anime_kuroshitsuji.jpg",
          title: "Тёмный дворецкий",
          timeCode: "5 серия (3 сезон)",
          redirectPage: "/darkButler",
          float: "auto"
        },
      }
    }
  },
  components: {
    VideoPreview
  },
  computed: {
    previewFloatControl() {
      return window.innerWidth < 630;
    }
  },
  mounted() {
    this.contentWidth = (window.innerWidth).toString() + "px";
  }

}
</script>
