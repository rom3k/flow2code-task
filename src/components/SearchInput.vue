<template>
  <form v-on:submit.prevent="submitSearch">
    <div class="field">
      <label class="label">Wyszukaj</label>
      <div class="control">
        <input
          class="input"
          type="text"
          placeholder="Wpisz frazę"
          v-model="searchQuery"
          @keyup="submitSearch"
        />
      </div>
      <p class="help is-danger" v-bind:style="{ display: displayProp }">
        Szukana fraza musi mieć przynajmniej 2 znaki
      </p>
    </div>
  </form>
</template>

<script>
export default {
  name: "SearchInput",
  data() {
    return { searchQuery: "", displayProp: "none" };
  },
  methods: {
    submitSearch: function() {
      if (this.searchQuery.length < 2) {
        this.displayProp = "block";
      } else {
        this.displayProp = "none";
        this.$emit("searchQuery", this.searchQuery);
      }
    }
  }
};
</script>
