<template>
  <app-layout>
    <v-container>
      <v-card class="mb-3 mx-auto transparent" flat @click="goToDashboard(12)">
        <v-card-text class="pa-0">
          <h1 class="title md-2 font-weight-bold">Despesas</h1>
          <div class="subheading font-weight-bold grey--text m-2">Veja para onde está indo seu dinheiro</div>
        </v-card-text>
      </v-card>

      <v-layout
        class="primary elevation-5"
        v-bind="binding"
        justify-center
        align-center
        fill-height
        wrap
      >
        <v-flex xs12>
          <entry-table
            entry-type="expense"
            :entries="expenses"
          ></entry-table>
        </v-flex>
      </v-layout>

    </v-container>
  </app-layout>
</template>

<script>
import AppLayout from '../components/AppLayout.vue'
import EntryTable from '../components/EntryTable.vue'

export default {
  data () {
    return {
      expenses: []
    }
  },
  created () {
    this.expenses = this.$store.state.expenses
  },
  computed: {
    binding () {
      const binding = {}
      if (this.$vuetify.breakpoint.smAndDown) binding.column = true
      return binding
    }
  },
  components: {
    'app-layout': AppLayout,
    'entry-table': EntryTable
  }
}
</script>

<style scoped>

</style>
