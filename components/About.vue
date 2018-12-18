<template>
  <section class="about-tera">
    <div class="container" style="text-align: center; padding-top: 32px;">
      <h2 class="text-header">About Tera</h2>
      <div class="content">
        <p style="text-align: justify" v-for="(item, index) in content" :key="index">
          {{item}}
        </p>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  data () {
    return {
      content: [
        'It is our great pleasure to invite you to join us to mine TERA, a coin that offers solutions for issues of existing cryptocurrencies, namely centralization, transaction throughput, transaction speed, confirmation times, transaction fees and general usability and difficulty of integration into existing payment and financial systems.',
        'We have managed to create a blockchain with 1 second block time, 8 seconds for full confirmation of transfer and zero fees. On top of that TERA blockchain is capable of throughput of 1000 transactions per second while retaining all praised blockchain features and bringing huge possibilities for further development and seamless integration with existing infrastructure as well as with new emerging technologies.',
        'Implementation of advanced blockchain features like smart contracts and decentralized messenger is in our roadmap and we plan to release these in near future.'
      ]
    }
  }
}
</script>
<style lang="sass">
.about-tera
  @media screen and (min-width: 600px) and (max-width: 959px)
    background-image: url('../static/images/toparrow.svg')
    height: 500px
    background-position: center
    background-repeat: no-repeat
    background-size: cover
  @media screen and (min-width: 960px) and (max-width: 1263px)
    background-image: url('../static/images/toparrow.svg') no-repeat center create fixed
    height: 400px
    background-position: center
    background-repeat: no-repeat
    background-size: cover
  @media screen and (min-width: 1264px)
    background-image: url('../static/images/toparrow.svg')
    height: 300px
    background-position: center
    background-repeat: no-repeat
    background-size: cover
</style>

