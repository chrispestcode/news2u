<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>

<template>
  <div class="header">
    Welcome to News2U!
  </div>
  <div class="main-content">
    <NewsListingCard />
    <SavedNewsListingCard />
  </div>
  <div class="footer">
    FOOTER
  </div>
</template>

<script>
import NewsListingCard from './NewsListingCard.vue'
import SavedNewsListingCard from './SavedNewsListingCard.vue'

export default {
  name: 'BaseCard',
  components: {
    NewsListingCard,
    SavedNewsListingCard
  },
  props: {
    msg: String
  }
}
</script>
