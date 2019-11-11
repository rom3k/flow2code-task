<template>
  <div class="columns is-centered">
    <div class="column is-one-quarter">
      <div class="box" v-bind:key="result.id" v-for="result in results">
        <p class="title is-4">{{ result.title }}</p>
        <article class="media">
          <div class="media-left">
            <img
              v-bind:src="
                'https://image.tmdb.org/t/p/w500' + result.poster_path
              "
            />
          </div>
          <div class="media-content">
            <div class="content">
              <p>
                <strong>Popularność:</strong>
                {{ result.popularity }}
              </p>
              <p>
                <strong>Liczba głosów:</strong>
                {{ result.vote_count }}
              </p>
            </div>
            <a class="button is-info">Więcej</a>
          </div>
        </article>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchResults",
  props: {
    results: {
      type: Array
    }
  }
};
</script>

<style lang="scss">
img {
  max-height: 200px;
}
</style>
