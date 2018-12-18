<template>
  <section id="roadmap" class="pt-section">
    <v-container>
      <div class="roadmap">
        <h2 class="text-header">Road map</h2>
        <div class="content">
          <div
            v-for="n in rowsCount"
            :key="n"
            :class="{'row-odd': n % 2 !== 0, 'row-even': n % 2 === 0, 'done': rowDone(n), 'last-row': n === rowsCount}"
          >
            <v-layout row wrap>
              <v-flex
                v-for="(item, index) in sliceItems(n)"
                :key="index"
                xs12
                :class="itemSize(n)"
              >
                <roadmap-item
                  :date="item.date"
                  :title="item.title"
                  :info="item.info"
                  :start-date="item.startDate"
                  :end-date="item.endDate"
                />
              </v-flex>
            </v-layout>
          </div>
        </div>
      </div>
    </v-container>
  </section>
</template>

<script>
import moment from 'moment'
import RoadmapItem from './RoadmapItem.vue'

export default {
  name: 'OurVision',
  components: {
    RoadmapItem
  },
  data () {
    return {
      itemsPerRow: 4,
      items: [
        {
          date: 'Oct 2018',
          startDate: '2018-10-01',
          endDate: '2018-10-31',
          title: 'Oct 2018',
          info: [
            'Smart-contracts'
          ]
        },
        {
          date: 'Nov 2018',
          startDate: '2018-11-01',
          endDate: '2018-11-30',
          title: 'Nov 2018',
          info: [
            'Decentralized forum.',
            'Decentralized stock exchange.'
          ]
        },
        {
          date: 'Dec 2018',
          startDate: '2018-12-01',
          endDate: '2018-12-31',
          title: 'Dec 2018',
          info: [
            'Web wallet'
          ]
        },
        {
          date: 'Q1 2019',
          startDate: '2019-01-01',
          endDate: '2019-03-31',
          title: 'Q1 2019',
          info: [
            'Android/iOS wallets',
          ]
        },
      ]
    }
  },
  computed: {
    rowsCount () {
      const itemList = this.items || []
      let row = Math.floor(itemList.length / this.itemsPerRow)
      if (itemList.length % this.itemsPerRow > 0) {
        return row + 1
      }
      return row
    }
  },
  methods: {
    sliceItems (rowIndex) {
      // rowIndex: 1-2-3
      const start = this.itemsPerRow * (rowIndex - 1)
      const end = this.itemsPerRow * (rowIndex)
      return this.items.slice(start, end)
    },
    itemSize (rowIndex) {
      const itemsLength = this.sliceItems(rowIndex).length
      return 'sm' + Math.ceil(12 / itemsLength)
    },
    lastRowItem (rowIndex) {
      const end = this.itemsPerRow * (rowIndex)
      return this.items.slice(end - 1, end)[0]
    },
    rowDone (rowIndex) {
      const lastItem = this.lastRowItem(rowIndex)
      if (lastItem) {
        return moment().unix() > moment(lastItem.endDate).unix()
      }
      return false
    }
  }
}
</script>

<style lang="sass">
.roadmap
  .row-even
    .roadmap-item
      &__line
        &.processing
          &:before
            width: 100%
</style>

<style lang="sass" scoped>

.roadmap
  .content
    &-title
      line-height: normal
      font-size: 40px
      text-align: center
      color: #FFFFFF
      margin: 2rem
  .row-odd, .row-even
    &.last-row
      &:after
        display: none
  .row-odd
    position: relative
    &:after
      content: ''
      position: absolute
      top: 28px
      right: -15px
      width: 15px
      height: calc(100% + 4px)
      border: 4px solid rgba(255, 255, 255, 0.25)
      border-left: none
      border-top-right-radius: 20px
      border-bottom-right-radius: 20px
    &.done
      &:after
        border-color: rgba(0,0,0,0.50)
  .row-even
    position: relative
    .layout.row
      flex-direction: row-reverse
    &:after
      content: ''
      position: absolute
      top: 28px
      left: -15px
      width: 15px
      height: calc(100% + 4px)
      border: 4px solid rgba(255, 255, 255, 0.25)
      border-right: none
      border-top-left-radius: 20px
      border-bottom-left-radius: 20px
    &.done
      &:after
        border-color: rgba(0,0,0,0.50)

@media screen and (max-width: 599px)
  .roadmap
    .row-odd
      &:after
        display: none
</style>
