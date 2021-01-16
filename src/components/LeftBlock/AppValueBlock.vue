<template>
  <div class="form-control">
    <label for="value">Значение</label>
    <textarea
      id="value"
      rows="3"
      ref="refValueBlock"
      @keyup="
        $emit(
          'setValueForTypeBlock',
          $event.target.value,
          this.$refs.refValueBlock
        )
      "
    ></textarea>
  </div>
</template>

<script>
export default {
  emits: {
    setValueForTypeBlock(value, ref) {
      if (value && ref) {
        return true
      }
      console.warn('No value or ref in setValueForTypeBlock emit')
      return false
    },
  },
}
</script>
