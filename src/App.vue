<template>
  <div id="app">
    <Categories />
  </div>
</template>

<script>
import Categories from '@/components/Views/Categories'
export default {
  name: 'App',
  components: { Categories },
  created() {
    if (!localStorage.getItem('language')) {
      localStorage.setItem('language', 'esp')
    }
  }
}
</script>
