<template>
  <section class="empty">
    <figure class="empty__icon">
      <img src="@/assets/empty.png" alt="Empty Image" />
    </figure>
    <p class="empty__text">{{text[language]}}</p>
  </section>
</template>

<script>
export default {
  name: 'P-Empty',
  props: {
    language: { default: 'esp'}
  },
  data() {
    return {
      text: {
        esp: 'No hay nada que mostrar',
        eng: 'There is no data'
      }
    }
  }
}
</script>

<style>
.empty {
  text-align: center;
}
.empty__icon {
  width: var(--space-lg);
  margin: var(--space-sm) auto;
}
.empty__text {
  color: var(--gray);
}
</style>