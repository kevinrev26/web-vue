<template>
  <section id="tech-spec">
    <div class="container" style="padding-top: 32px;">
      <h2 class="text-header" style="text-align: left;">Specification</h2>
        <v-data-table
          hide-headers
          hide-actions
          :items="data">
          <template slot="items" slot-scope="props">
            <td class="text-xs-center">
              <span v-if="props.item.id === 1 ||
                props.item.id ===3" class="table-header">
                {{props.item.col1}}
              </span>
              <span v-else>
                {{props.item.col1}}
              </span>
            </td>
            <td class="text-xs-center">
              <span v-if="props.item.id === 1 ||
                props.item.id ===3" class="table-header">
                {{props.item.col2}}
              </span>
              <span v-else>
                {{props.item.col2}}
              </span>
            </td>
            <td class="text-xs-center">
              <span v-if="props.item.id === 1 ||
                props.item.id ===3" class="table-header">
                {{props.item.col3}}
              </span>
              <span v-else-if="props.item.id === 4">
                <a :href="props.item.col3" target="_blank">{{props.item.col3}}</a>
              </span>
              <span v-else>
                {{props.item.col3}}
              </span>
            </td>
            <td class="text-xs-center">
              <span v-if="props.item.id === 1 ||
                props.item.id ===3" class="table-header">
                {{props.item.col4}}
              </span>
              <span v-else-if="props.item.id === 4">
                <a :href="props.item.col4" target="_blank">{{props.item.col4}}</a>
              </span>
              <span v-else>
                {{props.item.col4}}
              </span>
            </td>
            <td class="text-xs-center">
              <span v-if="props.item.id === 1 ||
                props.item.id ===3" class="table-header">
                {{props.item.col5}}
              </span>
              <span v-else>
                {{props.item.col5}}
              </span>
            </td>
          </template>
        </v-data-table>
    </div>
  </section>
</template>
<script>
export default {
  data () {
    return {
      data: [
        {
          id: 1,
          col1: 'Max Supply',
          col2: 'Issue Date',
          col3: 'Consensus Protocol',
          col4: 'Type',
          col5: 'Cryptographic Algorithm'
        },
        {
          id: 2,
          col1: '1,000,000,000',
          col2: '07/01/2018',
          col3: 'POW',
          col4: 'COIN',
          col5: 'TERAhash'
        },
        {
          id: 3,
          col1: 'Block Size',
          col2: 'Pre-mine',
          col3: 'Source Code',
          col4: 'Explorer',
          col5: 'Platform'
        },
        {
          id: 4,
          col1: '120 KB',
          col2: '5%',
          col3: 'https://github.com/tera',
          col4: 'http://terafoundation.org',
          col5: 'NodeJS'
        }
      ]
    }
  }
}
</script>
<style lang="sass">
#tech-spec
  .table-header
    color: #000
    font-weight: 500
</style>
