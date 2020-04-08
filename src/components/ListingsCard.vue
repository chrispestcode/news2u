<template>
  <div class="bg-light">
      <ul class="nav nav-pills">
        <li><a href='#' class="nav-link" id="news-tab-link"
              @click="handleNewsClick"
              :class="{active: isCurrentNews}">
                  News
            </a>
        </li>
        <li><a href='#'  class="nav-link" id="saved-tab-link"
            @click="handleSavedClick"
            :class="{active: !isCurrentNews}">
                  Saved
           </a>
        </li>
      </ul>
    <NewsListingsCard
        v-if="isCurrentNews"
        />
    <SavedNewsListingsCard
        v-if="!isCurrentNews"
        />
  </div>
</template>

<script>
import NewsListingsCard from './NewsListingsCard.vue'
import SavedNewsListingsCard from './SavedNewsListingCard.vue'

export default {
  name: 'ListingsCard',
  components: {
    NewsListingsCard,
    SavedNewsListingsCard
  },
  data () {
    return {
      isCurrentNews: true,
      savedNews: {}
    }
  },
  methods: {
    handleSavedClick: function() {
       this.isCurrentNews = false
    },
    handleNewsClick: function() {
       this.isCurrentNews = true
    },
    containsKey(obj, key){
      return Object.keys(obj).includes(key)
    }
  }
}
</script>
