<template>
  <div class="toolbar">
    <v-toolbar
    >
      <nuxt-link to="/"><img src="/images/Tera_Text.svg" alt="logo" class="logo"></nuxt-link>
      <v-toolbar-items class="hidden-sm-and-down" style="margin-left: 60px;">
        <v-btn v-for="(item, index)  in nav" :class="{ 'menu-item-active': item.active }" :key="index" @click="handleMenuItemClick(item.id)" flat>{{ item.title }}</v-btn>
      </v-toolbar-items>
      <v-spacer />
      <v-toolbar-side-icon
        class="hidden-md-and-up"
        @click.stop="rightDrawer = !rightDrawer">
      </v-toolbar-side-icon>
    </v-toolbar>

    <v-navigation-drawer
      :right="right"
      v-model="rightDrawer"
      temporary
      fixed>
      <v-list>
        <v-list-tile
          v-for="(item, index) in nav"
          :key="index"
          @click="handleMenuItemClick(item.id)">
          <v-list-tile-title>
            {{ item.title }}
          </v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>

export default {
  data () {
    return {
      active: false,
      clipped: false,
      right: true,
      rightDrawer: false,
      nav: [
        {
          id: 1,
          title: 'Technology',
          link: '',
          hashTag: '#tech-spec',
          active: false
        },
        {
          id: 2,
          title: 'Start Mining',
          link: 'https://github.com/terafoundation/wallet/',
          hashTag: '',
          active: false
        },
        {
          id: 3,
          title: 'Explorer',
          link: 'http://terafoundation.org/explorer.html',
          hasTag: '',
          active: false
        },
        {
          id: 4,
          title: 'Wallet',
          link: 'http://terafoundation.org/web-wallet.html',
          hashTag: '',
          active: false
        },
        {
          id: 5,
          title: 'Network Map',
          link: 'http://terafoundation.org/map.html',
          hashTag: '',
          active: false
        }
      ]
    }
  },
  methods: {
    closeMenu () {
      this.rightDrawer = false
    },
    handleMenuItemClick (id) {
      this.nav.map((item) => {
        if (item.id === id) {
          item.active = true
          if (item.hashTag !== '' && document.querySelector(item.hashTag)) {
            this.$vuetify.goTo(item.hashTag)
            this.closeMenu()
          } else if (item.link !== '') {
            this.closeMenu()
            window.open(item.link, '_blank')
          }
        } else {
          item.active = false
        }
      })
    }
  }
}
</script>

<style lang="sass">

nav.v-toolbar
  background-color: transparent !important
  box-shadow: none
  .v-toolbar__content,
  .v-toolbar__extension
    padding: 0 8rem !important
    @media screen and (max-width: 959px)
      padding: 0 32px !important
    @media screen and (max-width: 599px)
      padding: 0 16px !important
      .v-list__tile__title
        font-size: 12px !important
    .v-btn:before
      opacity: 0 !important
@media screen and (max-width: 959px)
  .v-list__tile__title
    font-size: 14px !important
@media screen and (max-width: 599px)
  .v-list__tile__title
    font-size: 12px !important
#google_translate_element
  .goog-te-combo
    background-color: rgb(248, 248, 248)
    border: 1px solid rgb(166, 166, 166)
    padding-left: 5px
.goog-te-banner-frame.skiptranslate
  display: none
.toolbar-dropdown-list
  padding: 0 !important
  &.theme--dark
    background-color: rgba(66, 66, 66, 0.8) !important
  .v-list__tile
    height: 38px !important
    line-height: 38px !important
.menu-item-active
  .v-btn__content
    &:after
      content: ""
      background: #000
      position: absolute
      bottom: -4px
      left: 0px
      height: 2px
      width: 50%

</style>
