<template>
  <form @submit.prevent="onSubmit">
    <BaseInput
      v-model="form.email"
      tyoe="email"
      name="loginEmail"
      placeholder="Introduce email..."
    />
    <BaseInput
      v-model="form.password"
      type="password"
      name="loginPassword"
      placeholder="Introduce contraseña"
    />

    <BaseButton type="submit" theme="primary">Iniciar Sesion</BaseButton>
  </form>
</template>

<script>
import BaseInput from '@/components/BaseInput.vue'
import BaseButton from '@/components/BaseButton.vue'

export default {
  name: 'LoginForm',
  components: { BaseInput, BaseButton },
  data() {
    return {
      form: {},
    }
  },
  methods: {
    onSubmit() {},
  },
}
</script>

<style lang="scss" scoped>
.login-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #c2d8f7;
  padding: 20px;
}
</style>
