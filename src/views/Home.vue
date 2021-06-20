<template>
  <div class="home">
    <ListComments />
  </div>
</template>
<script>
/*
Imports
*/

import ListComments from "../components/ListComments.vue";

export default {
  name: "Home",
  components: {
    ListComments
  }
};
</script>
