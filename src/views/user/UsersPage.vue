<template>
  <div class="addUser">
    <router-link class="link" :to="{ name: 'UserAdd' }">Добавить нового пользователя</router-link>
  </div>
  <h2>Список пользователя</h2>
  <div class="cards">
    <user-list v-for="user in users" :user="user" :key="user.userId" @delete-user="DeleteUser">
    </user-list>
  </div>
</template>

<script setup lang="ts">
import UserList from '@/components/UserList.vue';
let users = JSON.parse(localStorage.getItem('users') as string);

const DeleteUser = (userId: number) => {
  const newUsers = users.filter((elem: any) => elem.userId !== userId);
  localStorage.setItem('users', JSON.stringify(newUsers));
  window.location.reload();
};
</script>

<style scoped>
.addUser {
  position: absolute;
  top: 30px;
  right: 140px;
}
.addUser a {
  color: white;
  text-decoration: none;
}
h2 {
  text-align: center;
  margin-bottom: 50px;
}
.cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
}
.link{
  position: relative;
  padding: 5px;
  box-sizing: border-box;
}
.link::after{
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 1px;
  background-color: brown;
  transition: all 3s ease; 

}
.link:hover::after{
  width: 100%;
}
</style>
