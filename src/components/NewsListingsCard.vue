<template>
  <div class="border flex" id="current-news">
    <div class="active-cyan-4 mb-4 justify-content-end">
      <input class="form-control custom-search-bar" type="text"
        placeholder="Search" id="news-searchbar"
        v-model="search" @keyup.enter="searchResults" />
      <button type="submit"  @click.prevent='searchResults'
        class="btn btn-primary btn">
          Search
      </button>
    </div>
    <ul class="row p-1 listings hide-scrollbar">
        <li class="col-md-3 col-xs-12 news-card card"
          is="NewsCard"
          v-for="item in items"
          :key="item.url"
          :item="item"
          :saved="containsKey(savedNews,item.url)"
          @onSaveNews="handleSaveNews"
          >
        </li>
      </ul>
  </div>
</template>

<script>
  import NewsCard from './NewsCard.vue'
  import axios from 'axios'

  export default {
    name: 'NewsListingsCard',
    components: {
      NewsCard
    },
    mounted () {
      axios
        .get(this.baseUrl + 'top-headlines?country=us&'+'apiKey='+this.apiKey)
        .then(response => {
          this.items = response.data.articles;
        })
        .catch((error) => {
            console.warn('Data could not be retrieved: ' + error);
        })
        if(localStorage.savedNews){
          this.savedNews = JSON.parse(localStorage.getItem('savedNews'))
        }
    },
    data() {
      return {
        items: [],
        baseUrl: 'http://newsapi.org/v2/',
        apiKey: '',
        search: '',
        savedNews: Object
      }
    },
    methods: {
      containsKey(obj, key){
        var result = Object.keys(obj).includes(key)
        return result
      },
      searchResults() {
        axios
          .get(this.baseUrl + 'everything?q='+ this.search +'&apiKey='+this.apiKey)
          .then(response => {
            this.items = response.data.articles;
          })
          .catch((error) => {      //did not have this and it was drastically slower on searching
              console.warn('Data could not be retrieved: ' + error);
          })
      },
      handleSaveNews(item) {
        if(!this.containsKey(this.savedNews, item.url)){
          this.savedNews = {[item.url]: item,...this.savedNews}
        }
        else {
          this.$delete(this.savedNews, item.url)
        }
      },
    },
    beforeDestroy() {
      localStorage.setItem('savedNews',JSON.stringify(this.savedNews))
    }
  }
</script>
