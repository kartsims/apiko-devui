<template>
  <div class="page padded">
    <div class="columns is-mobile">
      <div class="column is-one-quarter"><CollectionsList linktodata="true"></CollectionsList></div>
      <div class="column">
        <div class="card">
          <div class="card-content">
            <div class="content">
              <p class="control has-addons is-pulled-right">
                <router-link class="button" active-class=" is-primary" :to="propertiesLink" exact>
                  <span class="icon is-small">
                    <i class="fa fa-align-left"></i>
                  </span>
                  <span>PROPERTIES <span v-if="showDocs">(STRUCTURE)</span></span>
                </router-link>
                <router-link class="button" active-class=" is-primary" :to="dataLink">
                  <span class="icon is-small">
                    <i class="fa fa-database"></i>
                  </span>
                  <span>CONTENT <span v-if="showDocs">(DATA)</span></span>
                </router-link>
              </p>
              <h1>{{this.$route.params.id}}</h1>
              <p v-if="showDocs">Here's the actual data of this collection.</p>
              <p>Haven't had time to implement this yet, hold on please (or use phpMyAdmin or someting to manage your data for now).</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CollectionsList from '../components/CollectionsList'
import { mapState } from 'vuex'

export default {
  components: {
    CollectionsList
  },
  computed: {
    dataLink () {
      return '/collections/' + this.$route.params.id + '/data'
    },
    propertiesLink () {
      return '/collections/' + this.$route.params.id
    },
    ...mapState(['showDocs'])
  }
}
</script>

<style scoped>
h1 {
  margin-top: 0;
  text-transform: uppercase;
}
</style>
