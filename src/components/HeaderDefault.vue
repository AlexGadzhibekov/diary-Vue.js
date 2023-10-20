<template>
  <div class="header">
    <div class="headerLogo"><img src="../assets/logo.svg" alt="" /></div>
    <ul class="headerMenu">
      <li class="link"><router-link :to="{ name: 'HomePage' }">Главная</router-link></li>
      <li class="link">
        <router-link :to="{ name: 'UsersList' }">Список Пользователей</router-link>
      </li>
      <li class="link"><router-link :to="{ name: 'LessonsList' }">Список Занятий</router-link></li>
    </ul>
  </div>
  <hr />
</template>

<script setup lang="ts"></script>

<style scoped>
.header {
  display: flex;
  align-items: center;
  gap: 50px;
  padding: 20px 0;
}
.headerLogo {
  width: 24px;
  height: 24px;
}
.headerMenu {
  display: flex;
  justify-content: space-between;
  list-style: none;
  gap: 20px;
}
.headerMenu a {
  color: white;
  text-decoration: none;
}
.link {
  position: relative;
  padding: 5px;
  box-sizing: border-box;
}
.link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 1px;
  background-color: #fff;
  box-shadow: 4px 4px 15px rgb(255, 255, 255);
  transition: all 1s ease;
}
.link:hover::after {
  width: 100%;
}
hr {
  box-shadow: 4px 4px 15px rgb(255, 255, 255);
  margin-bottom: 20px;
}
</style>
