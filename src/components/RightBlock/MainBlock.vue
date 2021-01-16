<template>
  <div class="card card-w70">
    <keep-alive>
      <component
        v-for="block in addedBlocks"
        :is="block.nameBlock"
        :key="block.nameBlock"
        :text="block.text"
      ></component>
    </keep-alive>
  </div>
</template>

<script>
import init from './InitBlock.vue'
import titleB from './TitleBlock.vue'
import avatar from './AvatarBlock.vue'
import subtitle from './SubTitleBlock.vue'
import textB from './TextBlock.vue'

export default {
  props: { addedBlocks: Array },

  components: {
    init,
    titleB,
    avatar,
    subtitle,
    textB,
  },
}
</script>
