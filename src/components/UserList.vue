<template>
  <div class="card">
    <router-link
      :to="{
        name: 'UserPage',
        params: {
          userId: props.user.userId
        }
      }"
      class="cardTitle"
    >
      <h2>{{ props.user.surname }} {{ props.user.name }}</h2>
    </router-link>
    <p>Дата рождения: {{ props.user.date }}</p>
    <p>Статус: {{ props.user.role }}</p>
    <div class="buttons">
      <router-link
        :to="{
          name: 'EditUserPage',
          params: {
            userId: props.user.userId
          }
        }"
        class="editBtn"
        >Редактировать</router-link
      >
      <button @click="emits('DeleteUser', Number(props.user.userId))">Удалить</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { User } from '@/types/user';
interface Props {
  user: User;
}
const props = defineProps<Props>();

interface Emits {
  (e: 'DeleteUser', userId: number): void;
  (e: 'EditUser', user: User): void;
}
const emits = defineEmits<Emits>();
</script>

<style scoped>
.card {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 10px;
  width: 300px;
  padding: 20px;
  background-color: #181818;
  box-shadow: 4px 4px 15px black;
  border-radius: 20px;
}
h2 {
  font-weight: 700;
  font-size: 20px;
}
p {
  font-size: 16px;
}
p:last-of-type {
  margin-bottom: 20px;
}
h2,
p {
  text-align: center;
}
.buttons {
  display: flex;
  justify-content: space-between;
  gap: 20px;
}
button,
.editBtn {
  margin-left: 10px;
  padding: 10px 20px;
  background: orangered;
  color: white;
  border: none;
  text-decoration: none;
  border-radius: 20px;
  border: 1px solid orangered;
  cursor: pointer;
}
button:hover,
.editBtn:hover{
  background: none;
  border: 1px solid orangered;
  color: orangered;
}
.cardTitle {
  color: white;
  text-decoration: none;
}
</style>
