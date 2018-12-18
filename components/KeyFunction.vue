<template>
  <section class="tera-feature">
    <div class="container" style="text-align: center; padding-top: 32px;">
      <h2 class="text-header">Key Features</h2>
      <v-layout align-center align-content-space-between row wrap>
        <v-flex xs12 sm6 md4 v-for="(item, index) in data" :key="index">
          <div class="feature-item">
            <div style="text-align: center; height: 100px">
              <img :src="item.src" alt='' style="margin-top: 16px;"/>
            </div>
            <h3 style="margin-bottom: 16px; margin-top: 16px;">{{item.title}}</h3>
            <p style="padding-left: 12px; padding-right: 12px; text-align: justify;">{{item.content}}</p>
          </div>
        </v-flex>
      </v-layout>
    </div>
  </section>
</template>
<script>
export default {
  data () {
    return {
      data: [
        {
          src: '/images/fast.svg',
          title: 'Fast Block Generation',
          content: 'TERA is fastest block genaration blockchain in decentralized blockchains. (Meaning that POS and the like are not decentralized...). With 1s block genaration and 8s to confirmation, your transaction is just edametaly'
        },
        {
          src: '/images/throughput.svg',
          title: 'High transaction throughput',
          content: 'TERA blockchain is capable of throughput of 1000 transactions per second while retaining all praised blockchain features and bringing huge'
        },
        {
          src: '/images/namely.svg',
          title: 'User-friendly',
          content: 'The coins are kept in accounts by analogy like bank accounts.'
        }
      ]
    }
  }
}
</script>
<style lang="sass">
.feature-item
  width: 290px
  height: 286px
  background: rgba(216,216,216,0.20)
  border-radius: 4px
  margin-top: 32px
  margin-left: auto
  margin-right: auto
  @media screen and (min-width: 600px)
    &:not(:last-child)
      margin-right: 32px
</style>
