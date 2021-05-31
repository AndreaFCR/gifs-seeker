<template>
  <input
    v-bind="$props"
    class="base-input"
    @input="changeValue($event)"
    @keyup.enter="$emit('keyup-enter')"
  />
</template>

<script>
export default {
  name: 'BaseInput',
  props: {
    value: {
      type: [String, Number],
      default: '',
    },
    type: {
      type: String,
      default: 'text',
      validate: (value) => ['type', 'number', 'email'].includes(value),
    },
    name: {
      type: String,
      required: true,
    },
    placeholder: {
      type: String,
      default: 'Escribe aquí...',
    },
  },
  methods: {
    changeValue(event) {
      this.$emit('input', event.target.value)
    },
  },
}
</script>
