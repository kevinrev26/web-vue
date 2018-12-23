<template>
  <section class="footer-tera">
    <div style="text-align: center; margin-top: 32px; margin-bottom: 40px;">
      <img src="/images/Tera_logo.svg" style="height: 56px" />
    </div>
    <div style="display: flex; justify-content: center;">
      <span
        class="footer-item"
        v-for="(item, index) in nav"
        :key="index"
        @click="handleMenuItemClick(item.id)">
          {{ item.title }}
      </span>
    </div>
    <div class="footer-social">
      <v-btn fab dark
        small
        color="#667586"
        v-for="item in data"
        :key="item.icon"
        @click="handleClick(item.link)"
        >
        <v-icon dark>{{`mdi-${item.icon}`}}</v-icon>
      </v-btn>
    </div>
  </section>
</template>
<script>
export default {
  data () {
    return {
      nav: [
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
      ],
      data: [
        {
          icon: 'facebook',
          link: 'fb.com'
        },
        {
          icon: 'twitter',
          link: 'twitter.com'
        },
        {
          icon: 'discord',
          link: 'discord.com'
        },
        {
          icon: 'github-circle',
          link: 'github.com'
        },
        {
          icon: 'telegram',
          link: 'telegram.com'
        }
      ]
    }
  },
  methods: {
    handleMenuItemClick (id) {
      this.nav.map((item) => {
        if (item.id === id) {
          if (item.hashTag !== '' && document.querySelector(item.hashTag)) {
            this.$vuetify.goTo(item.hashTag)
          } else if (item.link !== '') {
            window.open(item.link, '_blank')
          }
        }
      })
    }
  }
}
</script>
<style lang="sass">
.footer-tera
  height: 264px
  background: #354154
  @media screen and (max-width: 959px) and (min-width: 600px)
    background: url('../static/images/bottomArrow.svg') no-repeat center center
    -webkit-background-size: cover
    -moz-background-size: cover
    -o-background-size: cover
    background-size: cover
  .footer-item
    color: #FFF
    cursor: pointer
    &:not(:last-child)
      margin-right: 32px
  .footer-social
    display: flex
    justify-content: center
    margin-top: 24px
</style>

