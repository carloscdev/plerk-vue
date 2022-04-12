<template>
  <section class="loader">
    <div class="loader__spinner"></div>
    <p class="loader__text">{{text[language]}}</p>
  </section>
</template>

<script>
export default {
  name: 'P-Loader',
  data() {
    return {
      text: {
        esp: 'Cargando',
        eng: 'Loading'
      },
      language: localStorage.getItem('language')
    }
  }
}
</script>

<style>
.loader {
  text-align: center;
}
.loader__spinner {
  width: var(--space-lg);
  height: var(--space-lg);
  margin: var(--space-sm) auto;
  border: 0.8rem solid var(--white);
  border-top: 0.8rem solid var(--primary);
  border-radius: 50%;
  animation: spinner 1s linear infinite;
}
.loader__text {
  color: var(--gray);
}

@keyframes spinner {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
</style>