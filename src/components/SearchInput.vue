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
          v-bind:class="{ 'is-danger': inputProp }"
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
    return { searchQuery: "", displayProp: "none", inputProp: false };
  },
  methods: {
    submitSearch: function() {
      setTimeout(() => {
        if (this.searchQuery.length == 0) {
          this.displayProp = "block";
          this.inputProp = true;
        } else {
          this.displayProp = "none";
          this.inputProp = false;
          this.$emit("searchQuery", this.searchQuery);
        }
      }, 500);
    }
  }
};
</script>
