<template>
  <div class="news-card">
    <button type="button" class="btn btn-primary save-button"
     @click="onSaveNews"  v-if="!saved">
    SAVE
    </button>
    <button type="button" class="btn btn-danger save-button"
    @click="onSaveNews" v-if="saved">
    UNSAVE
    </button>
    <a :href=item.url target="_blank">
      <img class="card-img-top" :src="item.urlToImage" :alt="item.description" />
      <div class="card-title font-weight-bold">{{item.title}}</div>
      <div class="card-text text-dark"> {{item.description}} </div>
    </a>
  </div>
</template>

<script>
  export default {
    name: 'NewsCard',
    props: {
      item: Object,
      saved: Boolean
    },
    methods: {
      onSaveNews() {
        this.$emit('onSaveNews', this.item)
      }
    }
  }
</script>
