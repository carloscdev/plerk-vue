<template>
  <section class="error">
    <figure class="error__icon">
      <img src="@/assets/error.png" alt="Empty Image" />
    </figure>
    <p class="error__text">{{ text[language] }}</p>
    <p class="error__button" @click="reloadData()">{{ button[language] }}</p>
  </section>
</template>

<script>
export default {
  name: 'P-Error',
  props: {
    language: { default: 'esp'}
  },
  data() {
    return {
      text: {
        esp: 'Ocurrió un error',
        eng: 'An error occurred'
      },
      button: {
        esp: 'Recargar datos',
        eng: 'Reload data'
      }
    }
  },
  methods: {
    reloadData() {
      this.$emit('reload')
    }
  }
}
</script>

<style>
.error {
  text-align: center;
}
.error__icon {
  width: var(--space-lg);
  margin: var(--space-sm) auto;
}
.error__text {
  color: var(--gray);
}
.error__button {
  color: var(--primary);
  margin-top: 2rem;
  cursor: pointer;
  border-bottom: 0.1rem solid var(--primary);
  display: inline-block;
}
</style>