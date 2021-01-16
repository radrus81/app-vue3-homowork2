<template>
  <div class="container column">
    <form class="card card-w30" @submit.prevent="addBlock">
      <app-type-block @selectedTypeBlock="setTypeBlock"></app-type-block>
      <app-value-block
        @setValueForTypeBlock="setValueForTypeBlock"
      ></app-value-block>
      <button class="btn primary" :disabled="isActivBtnAdd">
        Добавить
      </button>
    </form>
    <main-block :addedBlocks="addedBlocks"></main-block>
  </div>
  <comment-block></comment-block>
</template>

<script>
import CommentBlock from './components/CommentBlock/MainCommentBlock.vue'
import AppTypeBlock from './components/LeftBlock/AppTypeBlock.vue'
import AppValueBlock from './components/LeftBlock/AppValueBlock.vue'
import MainBlock from './components/RightBlock/MainBlock.vue'

export default {
  data() {
    return {
      typeBlock: 'titleB',
      valueForBlock: '',
      isAddUserBlock: false,
      addedBlocks: [{ nameBlock: 'init', text: null }],
      refTypeBlock: null,
      refValueBlock: null,
    }
  },
  components: {
    AppTypeBlock,
    AppValueBlock,
    MainBlock,
    CommentBlock,
  },
  methods: {
    setTypeBlock(typeBlock, refTypeBlock) {
      this.typeBlock = typeBlock
      this.refTypeBlock = refTypeBlock //запоминаю ref ссылку, чтобы после добавления почистить, не смог придумать способ получше
    },
    setValueForTypeBlock(value, refValueBlock) {
      this.valueForBlock = value
      this.refValueBlock = refValueBlock //для значения также
    },
    addBlock() {
      if (!this.isAddUserBlock) {
        this.isAddUserBlock = true
        this.addedBlocks.length = 0
      }
      this.addedBlocks.push({
        nameBlock: this.typeBlock,
        text: this.valueForBlock,
      })
      this.typeBlock = 'titleB'
      this.valueForBlock = ''
      if (this.refTypeBlock) {
        this.refTypeBlock.value = this.typeBlock //очистка
      }
      this.refValueBlock.value = this.valueForBlock
    },
  },
  computed: {
    isActivBtnAdd() {
      return this.valueForBlock.length > 3 ? false : true
    },
  },
}
</script>

<style>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
