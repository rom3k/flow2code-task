<template>
  <div id="root">
    <search-input v-on:searchQuery="fetchQuery" />
    <search-results
      :results="results"
      :isAllowedForChecking="isAllowedForChecking"
    />
  </div>
</template>

<script>
import SearchInput from "./components/SearchInput.vue";
import SearchResults from "./components/SearchResults.vue";
import axios from "axios";

export default {
  name: "app",
  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/movie",
      apiKey: "8673a6b0eccdac7514050448c45f7d1a",
      apiLang: "pl",
      results: [],
      isAllowedForChecking: false
    };
  },
  components: {
    SearchInput,
    SearchResults
  },
  methods: {
    fetchQuery: function(searchQuery) {
      let request = `${this.apiUrl}?api_key=${this.apiKey}&language=${this.apiLang}&query=${searchQuery}&include_adult=false`;
      this.getMovies(request);
    },
    getMovies: function(req) {
      axios.get(req).then(res => {
        this.results = res.data.results;
        this.isAllowedForChecking = true;
      });
    }
  }
};
</script>
