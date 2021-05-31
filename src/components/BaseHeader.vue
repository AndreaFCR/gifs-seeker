<template>
  <header>
    <div class="header-title">
      <img src="@/assets/icons/gif.svg" alt="find gifs logo" />
      <h2>Gifs Seeker</h2>
    </div>
  </header>
</template>

<script>
export default {
  name: 'BaseHeader',
}
</script>

<style lang="scss" scoped>
header {
  display: flex;
  justify-content: space-between;
  width: 100%;
  padding: 0 15px;
}
.header-title {
  display: flex;
  align-items: center;
  width: 100%;
  img {
    width: 50px;
    height: 50px;
  }
}
</style>
