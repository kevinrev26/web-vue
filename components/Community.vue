<template>
  <div class="tera-community text-xs-center">
    <v-btn fab dark
      :small="$vuetify.breakpoint.smAndDown"
      :large="$vuetify.breakpoint.xlOnly"
      color="#667586"
      v-for="item in data"
      :key="item.icon"
      @click="handleClick(item.link)"
      >
      <v-icon dark>{{`mdi-${item.icon}`}}</v-icon>
    </v-btn>
  </div>
</template>
<script>
export default {
  data () {
    return {
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
    handleClick (url) {
      window.open(url, '_blank')
    }
  }
}
</script>
<style lang="sass">
.tera-community
  position: absolute
  left: 0
  right: 0
  bottom: 20px
  @media screen and (max-width: 599px)
    top: 300px
  @media screen and (max-width: 530px)
    top: 270px
  @media screen and (max-width: 490px)
    top: 240px
  @media screen and (max-width: 440px)
    top: 210px
  @media screen and (max-width: 400px)
    top: 190px
</style>
