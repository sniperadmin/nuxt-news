<template>
  <div class="container mt-5">
    <div class="container">
      <b-row>
        <b-col v-for="(article, index) in articles" :key="index" md="4">
          <b-card
            :title="article.title"
            :img-src="article.urlToImage"
            :img-alt="article.title"
            img-top
            style="max-width: 20rem;"
            class="mb-2"
          >
            <b-card-text>
              {{ article.description }}
            </b-card-text>

            <b-button :href="article.url">
              more info
            </b-button>
          </b-card>
        </b-col>
      </b-row>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData ({
    app
  }) {
    const {
      articles
    } = await app.$axios.$get(
      `https://newsapi.org/v2/top-headlines?language=ar&apiKey=${process.env.API_KEY}`
    )
    return {
      articles
    }
  }
}

</script>

<style>

</style>
