<template>
  <section class="categoryItem">
    <figure>
      <img :src="category.image" :alt="category.name.esp" @error="validateImage" />
    </figure>
    <div>
      <small>{{ getCategoryType(category.category_type) }}</small>
      <h2>{{ category.name[language] || category.name['esp'] }}</h2>
      <p>{{ category.description[language] || category.description['esp'] }}</p>
    </div>
  </section>
</template>

<script>
export default {
  name: 'P-Category-Item',
  props: {
    category: {
      type: Object,
      default: () => {}
    }
  },
  data() {
    return {
      language: localStorage.getItem('language')
    }
  },
  methods: {
    validateImage(e) {
      e.target.src = require('@/assets/not-found.png')
    },
    getCategoryType(type) {
      switch(type) {
        case 1: return 'Normal'
        case 2: return this.language === 'esp' ? 'Libre' : 'Free'
        case 3: return this.language === 'esp' ? 'Personalizada' : 'Customized'
        default: return '---'
      }
    }
  }
}
</script>

<style>
.categoryItem {
  background-color: var(--white);
  display: flex;
  align-items: center;
  gap: var(--space-sm);
  padding: var(--space-sm);
  border-radius: var(--rounded);
  transition: box-shadow 0.1s ease-in-out;
  overflow: hidden;
}
.categoryItem:hover {
  box-shadow: var(--shadow);
}
.categoryItem figure{
  width: 25%;
  min-width: var(--space-lg);
}
.categoryItem figure img {
  border-radius: var(--rounded);
}
.categoryItem p {
  white-space: nowrap;
  text-overflow: ellipsis;
  width: 20rem;
  max-width: 100%;
  overflow: hidden;
  margin: 0.2rem 0;
}
.categoryItem small {
  font-size: 1.2rem;
  color: var(--gray);
}
</style>