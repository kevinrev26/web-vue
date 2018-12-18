<template>
  <div id="app" ref="app">
    <v-app id="inspire">
      <tera-header />
      <about-tera />
      <key-function />
      <tech-spec />
      <tera-roadmap />
      <tera-footer />
    </v-app>
  </div>
</template>
<script>
import TeraHeader from '~/components/Header'
import AboutTera from '~/components/About'
import KeyFunction from '~/components/KeyFunction'
import TechSpec from '~/components/Spec'
import TeraRoadmap from '~/components/Roadmap'
import TeraFooter from '~/components/Footer'

export default {
  components: {
    TeraHeader,
    AboutTera,
    KeyFunction,
    TechSpec,
    TeraRoadmap,
    TeraFooter
  }
}
</script>

