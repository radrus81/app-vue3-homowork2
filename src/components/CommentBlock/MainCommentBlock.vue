<template>
  <div class="container">
    <p v-if="!isLoadComments">
      <button class="btn primary" @clicK="loadComments">
        Загрузить комментарии
      </button>
    </p>
    <div class="card" v-else>
      <h2>Комментарии</h2>
      <comment-block :dataComments="dataComments"></comment-block>
    </div>
    <div class="loader" v-if="loading"></div>
  </div>
</template>

<script>
import axios from 'axios'
import CommentBlock from './CommentBlock.vue'
export default {
  data() {
    return {
      isLoadComments: false,
      dataComments: [],
      loading: false,
    }
  },
  methods: {
    async loadComments() {
      this.loading = true
      try {
        const { data } = await axios.get(
          `https://jsonplaceholder.typicode.com/comments?_limit=42`
        )
        setTimeout(() => {
          this.dataComments = data
          this.loading = false
          this.isLoadComments = true
        }, 1500)
      } catch (e) {
        console.log(e.message)
      }
    },
  },

  components: {
    CommentBlock,
  },
}
</script>
