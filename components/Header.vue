<template>
  <section class="tera-header">
    <toolbar />
    <community />
  </section>
</template>
<script>
import Toolbar from './Toolbar'
import Community from './Community'

export default {
  components: {
    Toolbar,
    Community
  }
}
</script>
<style lang="sass" scoped>
.tera-header
  position: relative
  background: url('../static/images/Tera_Web_BG.png') center center no-repeat
  @media screen and (min-width: 600px)
    height: 100vh
  @media screen and (max-width: 599px)
    display: inline-block
    height: 400px
    background: url('../static/images/Tera_Web_BG.png') no-repeat
    background-size: contain, cover
  @media screen and (max-width: 550px)
    height: 350px
  @media screen and (max-width: 500px)
    height: 320px
  @media screen and (max-width: 460px)
    height: 300px
</style>

