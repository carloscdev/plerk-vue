<template>
  <section class="language">
    <span
      :class="language == 'esp' && 'active'"
      @click="changeLanguage('esp')"
    >
      ESP
    </span>
    |
    <span
      :class="language == 'eng' && 'active'"
      @click="changeLanguage('eng')"
    >
      ENG
    </span>
  </section>
</template>

<script>
export default {
  name: 'P-Language',
  data() {
    return {
      language: 'esp'
    }
  },
  created() {
    this.getCurrentLanguage()
  },
  methods: {
    changeLanguage(lng) {
      localStorage.setItem('language', lng)
      this.getCurrentLanguage()
      window.location.reload()
      // this.$emit('reload')
    },
    getCurrentLanguage() {
      this.language = localStorage.getItem('language')
    }
  }
}
</script>

<style>
.language {
  text-align: right;
  margin-bottom: 2.5rem;
    font-size: 1rem;
}
.language span {
  cursor: pointer;
  color: var(--gray);
}
.language .active {
  font-weight: bold;
  color: var(--primary);
}
</style>