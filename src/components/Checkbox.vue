<template>
  <div class="ui checkbox"
  :class="classData"
  tabindex="-1"
  @click="onClick"
  >
    <input type="checkbox" class="hidden"
    :checked="modelValue"
    tabindex="0"
    >
    <label>
      <slot></slot>
    </label>
  </div>
</template>

<script>
//
// = COMPNONT
//
export default {
  name: 'suCheckbox',
  model: {
    prop: 'modelValue',
    event: 'updateModel'
  },
  //
  // == props
  props: ['id', 'name', 'modelValue', 'disabled'],
  //
  // == computed
  computed: {
    isDisabled () {
      return this.disabled !== undefined && this.disabled !== false
    },
    classData () {
      return {
        checked: this.modelValue,
        disabled: this.isDisabled
      }
    }
  },
  //
  // == methods
  methods: {
    onClick (where) {
      if (!this.isDisabled) {
        this.$emit('updateModel', !this.modelValue)
      }
    }
  }
}
</script>
