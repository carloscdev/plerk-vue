<template>
  <section class="search">
    <input
      class="search__input"
      :placeholder="text[language]"
      @input="changeValue"
    />
  </section>
</template>

<script>
export default {
  name: 'P-Search',
  props: {
    language: { default: 'esp'}
  },
  data() {
    return {
      text: {
        esp: 'Buscar por nombre',
        eng: 'Search by name'
      },
    }
  },
  methods: {
    changeValue (event) {
      this.$emit('input', event.target.value);
    },
  }
}
</script>

<style>
.search {
  text-align: center;
}
.search__input {
    background-color: var(--white);
    border-width: 0.15rem;
    border-color: transparent;
    height: var(--space-lg);
    width: 40rem;
    max-width: 100%;
    padding: var(--space-sm);
    border-radius: var(--rounded);
}
.search__input:focus {
  outline: none;
  box-shadow: var(--shadow);
}
</style>