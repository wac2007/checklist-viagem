<template>
  <div class="container" id="app">
    <div class="title">
      <h1>Checklist de Viagem</h1>
      <p class="text-muted">Vai viajar e não quer esquecer nada? Confira os itens abaixo para lembrar o que levar em sua viagem!</p>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
  .title {
    margin-top: 20px;
    text-align: center;
  }
</style>
