<template>
  <div>
    <ul class="pagination">
      <li
        class="page-item"
        :class="{active: currentPage === page}"
        v-for="page in pages"
        :key="page"
      >
        <router-link class="page-link" :to="{path: url, query: {page: page}}">
          {{ page }}
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import { range } from '@/helpers/utils';

export default {
 name: 'McvPagintaion',
 props: {
  total: {
    type: Number,
    required: true
  },
  limit: {
    type: Number,
    required: true
  },
  currentPage: {
    type: Number,
    required: true
  },
  url: {
    type: String,
    required: true
  }
 },
 computed: {
  pages() {
    const pageCount = Math.ceil(this.total / this.limit)
    return range(1, pageCount)
  }
 }
}
</script>
