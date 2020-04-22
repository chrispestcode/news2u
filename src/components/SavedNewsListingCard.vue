<template>
  <div class="border flex" id="saved-news">
    <div class="active-cyan-4 mb-4 justify-content-end">
      <input class="form-control custom-search-bar" v-model="search" id="save-filter"
        type="text" placeholder="Filter saved news">
    </div>
    <ul class="row p-3 overflow-auto listings" id="save-content">
      <li class="col-md-3 col-xs-12 news-card card"
        is="NewsCard"
        v-for="item in filteredSavedNews"
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
      savedNews: []
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
      console.log((Object.keys(this.savedNews)))/*
      /* if(!(this.savedNews == 'Function')){
      return this.savedNews.filter(item => {
           return item.url.toLowerCase().indexOf(this.search.toLowerCase()) > -1
        }) */

        return this.savedNews
    }
  },
  mounted() {
    if(localStorage.savedNews){
      this.savedNews = JSON.parse(localStorage.getItem('savedNews'))
    }
  }
}
</script>
