<template>
  <div class="tweet-list">
    <div class="grid">
      <Tweet
        class="grid__item"
        v-for="tweet in tweets"
        :key="tweet.id"
        :item="tweet"
      />
    </div>
  </div>
</template>

<script>
import { OK } from '../util'
import Tweet from '../components/Tweet.vue'

export default {
  components: {
    Tweet
  },
  data () {
    return {
      tweets: []
    }
  },
  methods: {
    async fetchTweets () {
      const response = await axios.get('/api/tweets')

      if (response.status !== OK) {
        this.$store.commit('error/setCode', response.status)
        return false
      }

      this.tweets = response.data.data
    }
  },
  watch: {
    $route: {
      async handler () {
        await this.fetchTweets()
      },
      immediate: true
    }
  }
}
</script>

<style scoped>
</style>