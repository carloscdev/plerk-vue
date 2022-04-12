<template>
  <div class="container">
    <Language />
    <Search v-model="categoriesSearch" :language="language" />
    <div class="sub_container">
      <Loader v-if="isLoading" :language="language" />
      <CategoriesList :categoriesList="categoriesFiltered" />
      <Empty v-if="isEmpty" :language="language" />
      <Error v-if="isError" :language="language" @reload="getCategoriesList" />
    </div>
  </div>
</template>

<script>
import Search from '@/components/Search'
import Loader from '@/components/Common/Loader'
import Language from '@/components/Common/Language'
import CategoriesList from '@/components/CategoriesList'
import Empty from '@/components/Common/Empty'
import Error from '@/components/Common/Error'
import { BASE_URL, TOKEN } from '@/utils/constans'
export default {
  name: 'P-Categories',
  components: {
    Loader,
    Language,
    Empty,
    Error,
    Search,
    CategoriesList
  },
  data() {
    return {
      categoriesSearch: '',
      categoriesList: [],
      categoriesFiltered: [],
      isLoading: false,
      error: false,
      language: localStorage.getItem('language')
    }
  },
  computed: {
    isEmpty() {
      return this.categoriesFiltered.length === 0 && !this.isLoading && !this.error
    },
    isError() {
      return this.error && !this.isLoading
    }
  },
  watch: {
    categoriesSearch() {
        this.filterCategories()
    }
  },
  created() {
    this.getCategoriesList()
  },
  methods: {
    async getCategoriesList() {
      try {
        this.isLoading = true
        this.categoriesFiltered = []
        const url = BASE_URL
        const params = {
          headers: {
            'Authorization': TOKEN
          }
        }
        const response = await fetch(url, params)
        const result = await response.json()
        this.categoriesList = result.data
        this.categoriesFiltered = result.data
      } catch (error) {
        this.error = true
        this.categoriesList = []
        this.categoriesFiltered = []
      }
      this.isLoading = false
    },
    filterCategories() {
      this.isLoading = true
      this.categoriesFiltered = this.categoriesList.filter((category) => {
        return category.name[this.language]?.toLowerCase().includes(this.categoriesSearch.toLowerCase())
      })
      this.isLoading = false
    }
  }
}
</script>
