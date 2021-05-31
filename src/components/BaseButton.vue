<template>
  <div>
    <button class="base-button" :class="theme" :type="type">
      <slot>{{ text }}</slot>
    </button>
  </div>
</template>

<script>
export default {
  name: 'BaseButton',
  data() {
    return {
      theme: '',
      type: '',
      text: 'Buscar',
    }
  },
}
</script>

<style></style>
