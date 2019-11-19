<template>
  <div class="columns is-centered">
    <div class="column is-two-fifths">
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
          <p
            class="help is-danger"
            v-bind:style="{ display: errorDisplayProp }"
          >
            Szukana fraza musi mieć przynajmniej 1 znak
          </p>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import _ from "lodash";
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
    submitSearchQuery: _.debounce(function() {
      if (this.searchQuery.length == 0) {
        this.inputDisplayProp = true;
        this.errorDisplayProp = "block";
      } else {
        this.inputDisplayProp = false;
        this.errorDisplayProp = "none";
        this.$emit("searchQuery", this.searchQuery);
      }
    }, 300),
    removeSearchQuery: function() {
      this.searchQuery = "";
      this.submitSearchQuery();
    }
  }
};
</script>

<style>
.control.has-icons-right .icon {
  pointer-events: initial !important; /*I know it's ugly */
}
.columns {
  margin: 1rem;
}
</style>
