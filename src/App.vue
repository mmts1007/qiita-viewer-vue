<template>
  <div class="container">
    <h1>すべての投稿</h1>
    <div v-show="items == null">
      <spinner></spinner>
    </div>
    <div v-show="items != null">
      <ul class="media-list">
        <hr>
        <qiita-item v-for="item in items" :key="item.id" :item="item"></qiita-item>
      </ul>
    </div>
  </div>
</template>

<script>
import Spinner from './components/Spinner'
import QiitaItem from './components/QiitaItem'

export default {
  name: 'app',
  components: {
    Spinner, QiitaItem
  },
  data() {
    return {
      items: null
    }
  },
  created() {
    var self = this

    fetch('https://qiita.com/api/v2/items').then((response) => {
      return response.json()
    }).then((json) => {
      self.items = json
    })
  }
}
</script>

<style>
</style>
