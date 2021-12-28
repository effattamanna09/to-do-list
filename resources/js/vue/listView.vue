<template>
  <div>
    <div v-for="(item, index) in items" :key="index">
      <list-item :item="item" class="item" 
      v-on:itemchange="$emit('reloadlist')"/>
    </div>
  </div>
</template>

<script>
// import listItem from "./listItem"

import listItem from "./listItem.vue";

export default {
  props: ["items"],
  components: {
      
    listItem,
  },
};
</script>

<style scoped>
.item {
  background: rgb(201, 198, 190);
  padding: 5px;
  margin-top: 5px;
}
</style>
