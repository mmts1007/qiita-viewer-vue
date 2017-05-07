<template>
  <div>
    <li class="media">
      <div class="media-left">
        <a :href="'http://qiita.com/' + item.user.id">
          <img class="media-object img-rounded" :src="item.user.profile_image_url" width="50">
        </a>
      </div>
      <div class="media-body">
        <strong class="media-heading">{{ item.user.id }}</strong>
        <h4>
          <a :href="item.url">
            {{ item.title }}
          </a>
          <button class="btn btn-default btn-sm pull-right" @click="toggle">
            Show more
          </button>
        </h4>
        <div class="body">
          <div v-html="item.rendered_body" v-show="showsBody"></div>
        </div>
      </div>
    </li>
    <hr>
  </div>
</template>

<script>
export default {
  props: ['item'],
  methods: {
    toggle() {
      this.showsBody = !this.showsBody
    }
  },
  data() {
    return {
      showsBody: false
    }
  }
}
</script>

<style>
hr {
  margin-top: 10px;
  margin-bottom: 10px;
}
.body{
  width: 750px;
}
</style>
