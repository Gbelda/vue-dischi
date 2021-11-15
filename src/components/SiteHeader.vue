<template>
  <header class="container-fluid">
    <div class="header">
      <img src="../assets/img/spotify.png" alt="" />
    </div>
  </header>
</template>

<script>
export default {};
</script>

<style lang='scss'>
@import "../assets/scss/variables.scss";
header {
  background-color: $secondary_bg;
  .header {
    height: 80px;
    line-height: 70px;
    padding-left: 20px;
    img {
      height: 60px;
    }
  }
}
</style>