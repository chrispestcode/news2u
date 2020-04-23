<template>
  <div class="border flex" id="saved-news">
    <div class="active-cyan-4 mb-4 justify-content-end">
      <input class="form-control custom-search-bar" v-model="search" id="save-filter"
        type="text" placeholder="Filter saved news">
    </div>
    <ul class="row p-3 overflow-auto listings hide-scrollbar" id="save-content">
      <li class="col-md-3 col-xs-12 news-card card"
        is="NewsCard"
        v-for="item in filteredSavedNews"
        :key="item.url"
        :item="item"
        :saved="containsKey(item.url)"
        @onSaveNews="handleUnsaveNews"
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
      savedNews: [],
      savedNewsStorage: {}
    }
  },
  methods: {
    handleUnsaveNews(item) {
        this.$delete(this.savedNewsStorage, item.url)
        this.savedNews.splice(this.savedNews.indexOf(item), 1);

    },
    containsKey(key){
      if (this.savedNewsStorage==null){
        return false;
      }
      return Object.keys(this.savedNewsStorage).includes(key)
    },
  },
  computed: {
    filteredSavedNews() {
       if(!(typeof(this.savedNew) == 'function')){
         return this.savedNews.filter(item => {
           return item.url.toLowerCase().indexOf(this.search.toLowerCase()) > -1
          })
        }
        return this.savedNews
    }
  },
  mounted() {
    if(localStorage.savedNews){
      this.savedNewsStorage = JSON.parse(localStorage.getItem('savedNews'))
      let test = this.savedNewsStorage
      this.savedNews = Object.keys(test).map((key) => {
          return test[key]
      })
      console.log("J + " + JSON.stringify(this.savedNewsStorage))
    }
  },
  beforeDestroy() {
      localStorage.setItem('savedNews',JSON.stringify(this.savedNewsStorage))
  }
}
</script>
