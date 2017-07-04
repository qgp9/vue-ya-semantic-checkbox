<template>
  <div class="ui radio checkbox"
  :class="classData"
  @click="onClick"
  >
    <input type="radio" tabindex="0" class="hidden"
    :checked="isChecked"
    :value="value"
    >
    <label>
      <slot></slot>
    </label>
  </div>
</template>

<script>
export default {
  name: 'suRadiobutton',
  model: {
    prop: 'model'
  },
  props: ['id', 'name', 'model', 'disabled', 'value'],
  computed: {
    isChecked () { return this.model === this.value },
    isDisabled () {
      return this.disabled !== undefined && this.disabled !== false
    },
    classData () {
      return {
        checked: this.isChecked,
        disabled: this.isDisabled
      }
    }
  },
  methods: {
    onClick () {
      if (!this.isDisabled) {
        this.$emit('input', this.value)
      }
    }
  }
}
</script>
