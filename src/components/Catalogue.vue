<template>
  <div class="catalogue">
    <div class="card-deck">
      <div class="item" v-for="entry in entries" v-bind:key="entry.id">
        <b-card :title=entry.title
                :img-src=cover(entry)
                :img-alt=entry.title
                img-left
                style="max-width: 15rem;"
                class="mb-2 shadow-lg p-3 mb-5 bg-white rounded">
          <p class="card-text">
            {{entry.description}}
          </p>
          <router-link :to="{ name: 'story', params: { id: entry.id } }">
            <b-button class="mx-auto" variant="primary">
              Read
            </b-button>
          </router-link>
        </b-card>
      </div>
    </div>
  </div>
</template>

<script>

import Story from './Story'

export default {
  name: 'Catalogue',
  components: {
    Story
  },
  data () {
    return {
      story: null
    }
  },
  props: {
    entries: {
      type: Object,
      required: true
    }
  },
  methods: {
    cover: function (entry) {
      return '/static/images/' + entry.cover
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.catalogue {
  padding: 3%;
}

.catalogue .item {

}

</style>
