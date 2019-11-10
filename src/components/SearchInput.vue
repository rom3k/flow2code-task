<template>
  <form v-on:submit.prevent="submitSearchQuery">
    <div class="field">
      <label class="label">Wyszukaj</label>
      <div class="control has-icons-right">
        <input
          class="input"
          type="text"
          placeholder="Wpisz frazę"
          v-model="searchQuery"
          v-bind:class="{ 'is-danger': inputDisplayProp }"
          @keyup="submitSearchQuery"
        />
        <span
          class="icon is-right"
          v-show="searchQuery"
          @click="removeSearchQuery"
        >
          <i class="fas fa-times"></i>
        </span>
      </div>
      <p class="help is-danger" v-bind:style="{ display: errorDisplayProp }">
        Szukana fraza musi mieć przynajmniej 1 znak
      </p>
    </div>
  </form>
</template>

<script>
export default {
  name: "SearchInput",
  data() {
    return {
      searchQuery: "",
      inputDisplayProp: false,
      errorDisplayProp: "none"
    };
  },
  methods: {
    submitSearchQuery: function() {
      if (this.searchQuery.length == 0) {
        this.inputDisplayProp = true;
        this.errorDisplayProp = "block";
      } else {
        this.inputDisplayProp = false;
        this.errorDisplayProp = "none";
        this.$emit("searchQuery", this.searchQuery);
      }
    },
    removeSearchQuery: function() {
      this.searchQuery = "";
    }
  }
};
</script>

<style>
.control.has-icons-right .icon {
  pointer-events: initial !important;
}
</style>
