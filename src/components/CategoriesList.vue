<template>
  <section class="categoriesList">
    <CategoryItem v-for="(category, index) in categoriesList" :key="index" :category="category" />
  </section>
</template>

<script>
import CategoryItem from '@/components/CategoryItem'
export default {
  name: 'P-Categories-List',
  props: {
    categoriesList: {
      type: Array,
      required: true
    }
  },
  components: {
    CategoryItem
  }
}
</script>
<style>
.categoriesList {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(27rem, 1fr));
  grid-auto-rows: minmax(10rem, 1fr);
  gap: var(--space-md);
}
</style>