<template>
  <div class="form-control">
    <label for="type">Тип блока</label>
    <select id="type" @change="handlerTypeBlock" ref="typeBlock">
      <option
        v-for="item in listTypeBlock"
        :value="item.value"
        :key="item.value"
        >{{ item.text }}</option
      >
    </select>
  </div>
</template>

<script>
export default {
  emits: {
    selectedTypeBlock(value, ref) {
      if (value && ref) {
        return true
      }
      console.warn('No value or ref in selectedTypeBlock emit')
      return false
    },
  },
  data() {
    return {
      listTypeBlock: [
        { value: 'titleB', text: 'Заголовок' },
        { value: 'subtitle', text: 'Подзаголовок' },
        { value: 'avatar', text: 'Аватар' },
        { value: 'textB', text: 'Текст' },
      ],
    }
  },
  methods: {
    handlerTypeBlock(event) {
      this.$emit('selectedTypeBlock', event.target.value, this.$refs.typeBlock)
    },
  },
}
</script>
