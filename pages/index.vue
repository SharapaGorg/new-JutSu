<template>
  <section class="section">
    <div class="box primary_back grid" style="position: relative; z-index : 1">

      <search :list=anime_list placeholder="e.g. Тёмный дворецкий" class = "col-start-2"/>

      <br/>
      <b-button style = "float : right; bottom : 7px" type = "is-success">Найти</b-button>
      <b-field>
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
    <div class="box secondary_back" style="position: relative; bottom : 35px; z-index : 0"><br>
      <VideoPreview url="https://gen.jut.su/uploads/animethumbs/anime_nanatsu-no-taizai.jpg" title="7 Смертных грехов"
                    time-code="16 серия (4 сезон)"
                    redirect-page="/"/>
    </div>
  </section>
</template>

<style>

.primary_back {
  background: #515b3b !important;
  color: white
}

.secondary_back {
  background: #1f1f1f !important;
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
      anime_list: ['Моя геройская академия', 'Магическая битва', 'Атака Титанов', 'Тёмный дворецкий'].sort()
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
    }
  },
  computed: {
    secondFieldCheck() {
      return (this.pwd.length < 9 && this.pwd !== "")
    }
  }
}
</script>
