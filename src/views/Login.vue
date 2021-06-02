<template>
  <section class="login-section">
    <LoginForm />
  </section>
</template>

<script>
import LoginForm from '@/components/LoginForm.vue'
export default {
  name: 'Login',
  components: {
    LoginForm,
  },
}
</script>

<style>
.login-section {
  display: flex;
  justify-content: center;
  padding: 40px 0;
}
</style>
