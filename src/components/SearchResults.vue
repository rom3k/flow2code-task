<template>
  <table class="table">
    <thead>
      <tr>
        <th>#</th>
        <th>Tytuł</th>
        <th>Popularność</th>
        <th>Liczba głosów</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="result in results" v-bind:key="result.id">
        <th>{{ result.id }}</th>
        <th>{{ result.title }}</th>
        <th>{{ result.popularity }}</th>
        <th>{{ result.vote_count }}</th>
      </tr>
    </tbody>
  </table>
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
