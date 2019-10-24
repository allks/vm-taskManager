<template>
  <div>
    <h2>Добро пожаловать</h2>
    <p>Эта страница создана не несёт никакой функциональной нагрузги, чтобы протестировать возможности приложения нажмите: Далее</p>
    <router-link to="/todos" class="link">Далее</router-link>
  </div>
</template>

<style scoped>
  h2{
    font-size: 30px;
    color: #224B7A;
  }
  p{
    max-width: 450px;
    margin: 30px auto;
    line-height: 25px;
  }

  .link{
    background-color: #4A76A8;
    color: #fff;
    padding: 10px 50px;
    text-decoration: none;
    border-radius: 5px;
  }
  .link:hover{
    background-color: #224B7A;
  }
</style>