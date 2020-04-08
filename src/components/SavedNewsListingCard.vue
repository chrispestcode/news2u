<template>
  <div class="border flex" id="saved-news">
    <div class="active-cyan-4 mb-4">
      <input class="form-control" v-model="search" id="save-filter"
        type="text" placeholder="Filter saved news">
    </div>
    <ul class="row p-3 overflow-auto listing" id="save-content">
      <li class="col-md-3 col-xs-12 news-card card"
        is="NewsCard"
        v-for="item in savedNews"
        :key="item.url"
        :item="item"
        :saved="containsKey(savedNews,item.url)"
        @onSaveNews="onSaveNews"
        >
      </li>
    </ul>
  </div>
</template>

<script>
import NewsCard from './NewsCard.vue'

export default {
  name: 'SavedNewsListingCard',
  components:{
    NewsCard
  },
  data() {
    return {
      search: '',
      savedNews: Object
    }
  },
  methods: {
    onSaveNews(item) {
      this.$emit("onSaveNews", item)
    },
    containsKey(obj, key){
      return Object.keys(obj).includes(key)
    },
  },
  computed: {
    filteredSavedNews() {
    return  Object.keys(this.savedNews)
        .map(key => this.savedNews[key])
        .filter(item => {
          item.title.toLowerCase().includes(this.search.toLowerCase())
      })
    }
  },
  mounted() {
    if(localStorage.savedNews){
      this.savedNews = JSON.parse(localStorage.getItem('savedNews'))
    }
  }
}
</script>
