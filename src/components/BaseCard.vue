<template>
  <div>
    <div class="">
      <div class="header py-5 font-weight-bold" id="page-header">
        <h1>Welcome to News2U!</h1>
      </div>
    </div>
    <ListingsCard />
    <div class="footer py-5 bg-info text-white" id="page-footer">
      The data collected and utilized is courtesy of NewsApi.org
    </div>
</div>
</template>

<script>
import ListingsCard from './ListingsCard.vue'

export default {
  name: 'BaseCard',
  components: {
    ListingsCard
  }
}
</script>
