<template>
  <div id="root">
    <search-input />
  </div>
</template>

<script>
import SearchInput from "./components/SearchInput.vue";

export default {
  name: "app",
  components: {
    SearchInput
  }
};
</script>
