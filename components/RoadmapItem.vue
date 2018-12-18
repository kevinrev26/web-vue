<template>
  <div class="roadmap-item">
    <div
      class="roadmap-item__line"
      :class="{'done': done, 'processing': processing}"
    >
      <span class="dot"></span>
    </div>
    <div class="roadmap-item__body">
      <div class="roadmap-item__date">
        {{ date }}
      </div>
      <div
        v-if="Array.isArray(info) && info.length > 0"
        class="roadmap-item__info"
      >
        <ul>
          <li
            v-for="(el, idx) in info"
            :key="idx"
          >
            {{ el }}
          </li>
        </ul>
      </div>

      <div v-else-if="title" class="roadmap-item__info">
        <ul><li>{{ title }}</li></ul>
      </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment'

export default {
  props: {
    date: {
      type: String,
      required: true,
      default: 'Q1/2018'
    },
    title: {
      type: String,
      default: ''
    },
    info: {
      type: Array,
      default: () => []
    },
    startDate: {
      type: String,
      required: true,
      default: '2018-01-01'
    },
    endDate: {
      type: String,
      required: true,
      default: '2019-12-31'
    }
  },
  computed: {
    done () {
      return moment().unix() > moment(this.endDate).unix()
    },
    processing () {
      return moment().unix() > moment(this.startDate).unix() && moment().unix() < moment(this.endDate).unix()
    }
  }
}
</script>

<style lang="sass" scoped>
.roadmap-item
  position: relative
  &__line
    height: 4px
    background-image: linear-gradient(to left, rgba(0, 0, 0, 0.25) 0%, rgba(255, 255, 255, 0.65) 100%)
    /*border-radius: 2px*/
    position: relative
    margin-top: 2rem
    margin-bottom: 2rem
    .dot
      position: absolute
      top: 50%
      left: 0
      transform: translate(0, -50%)
      content: ''
      width: 20px
      height: 20px
      background-color: #fff
      border-radius: 50%
    &.done, &.processing
      &:before
        content: ''
        position: absolute
        top: 0
        left: 0
        width: 100%
        height: 100%
        /*border-radius: 2px*/
        background-color: rgba(0,0,0,0.50)
      .dot
        border: 6px solid rgba(0,0,0,0.50)
    &.processing
      &:before
        width: 5%
      .dot
        border-width: 4px
  &__body
    .roadmap-item__date
      font-size: 16px
      margin-bottom: 0.5rem
    .roadmap-item__info
      /*max-width: 13rem*/
      max-width: 85%
      background-color: rgba(255, 255, 255, 0.1)
      border-radius: 4px
      padding: 0.5rem 0.5rem 0.5rem 0
      margin-bottom: 2rem
      li
        font-size: 12px
        margin-bottom: 0.5rem

@media screen and (max-width: 599px)
  .roadmap-item
    display: flex
    height: 100%
    &__line
      width: 4px
      height: 100%
      margin: 0 18px 0 10px
      background-image: linear-gradient(rgba(255, 255, 255, 0.65) 0%, rgba(0, 0, 0, 0.25) 100%)
      .dot
        top: 0
        left: 50%
        transform: translate(-50%, 0)
      &.done, &.processing
        &:before
          top: 10px
          left: 0
      &.processing
        &:before
          width: 100%
          height: 6%
    &__body
      width: 100%
      padding-bottom: 15px
      .roadmap-item__info
        max-width: 100%
        width: 100%
</style>
