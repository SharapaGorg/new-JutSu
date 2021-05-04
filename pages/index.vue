<template>
  <section>
    <div class="box primary_back index-header" :style="{ 'max-width' : this.contentWidth }">
      <search :list=anime_list placeholder="e.g. Тёмный дворецкий" class="col-start-2"/>
      <br/>
      <b-button style="float : right; bottom : 7px" type="is-success">Найти</b-button>
      <b-field style="color: #bee6c3">
        <b-switch v-model="isSwitchedCustom"
                  true-value="Войти на сайт"
                  false-value="Шакалить">
          {{ isSwitchedCustom ? 'Войти на сайт' : 'Шакалить' }}
        </b-switch>
      </b-field>
      <b-modal v-model='isSwitchedCustom' v-if="isSwitchedCustom !== 'Шакалить'" has-modal-card aria-role="dialog"
               aria-modal :destroy-on-hide="false" trap-focus aria-label="Example Modal">
        <center>
          <div class="box secondary_back" style="width: 300px">
            <b-field>
              <b-input placeholder="Логин или email" v-model="loginEmail">
              </b-input>
            </b-field>
            <b-field :type="{ 'is-warning' : secondFieldCheck }">
              <b-input placeholder="Пароль" type="password" v-model="pwd">
              </b-input>
            </b-field>
            <b-button :loading="this.isSwitched" @click="userLogIn" class="is-primary" style="width: 85%">Вход
            </b-button>
          </div>
        </center>
      </b-modal>
    </div>
    <div class="box secondary_back index-content"
         :style="{ 'max-width' : this.contentWidth }"><br>
      <div v-for="preview in previews" :key="preview.title" class="anime_item" :style="{ 'float' : preview.float }">
        <VideoPreview :url="preview.url" :title="preview.title" :redirect-page="preview.redirectPage"
                      :time-code="preview.timeCode"/>
      </div>
    </div>
  </section>
</template>

<style>

.primary_back {
  background: #515b3b !important;
  color: white;
}

.secondary_back {
  background: #1f1f1f !important;
}

div.index-header {
  position: relative;
  align-items: center;
  z-index: 1;
  margin: auto;
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

import Search from '~/components/search'
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
    Search,
    VideoPreview
  },
  methods: {
    userLogIn() {
      this.isSwitched = true;
      // back end req
      this.isSwitched = false;
      // window.$nuxt.$router.push('/') NO
      // check for req ans, if success :
      this.isSwitchedCustom = "Шакалить"
      this.loginEmail = ""
      this.pwd = ""
    }
  },
  computed: {
    secondFieldCheck() {
      return (this.pwd.length < 9 && this.pwd !== "")
    }
  },
  mounted() {
    this.contentWidth = (window.innerWidth - 980).toString() + "px";
  }
}
</script>
