<template>
  <div class="editPage">
    <router-link :to="{ name: 'UsersList' }" class="returnBack link">Отмена</router-link>
    <my-input label="Имя: " placeholder="Введите имя" v-model="newUser.name" type="text"></my-input>
    <my-input
      label="Фамилия: "
      placeholder="Введите фамилию"
      v-model="newUser.surname"
      type="text"
    ></my-input>
    <my-input
      label="Дата: "
      placeholder="Введите дату рождения"
      type="date"
      v-model="newUser.date"
    ></my-input>
    <my-input
      label="Роль: "
      placeholder="Введите вашу роль"
      type="text"
      v-model="newUser.role"
    ></my-input>
    <router-link :to="{ name: 'UsersList' }" @click="editLocalStorage">Сохранить</router-link>
  </div>
</template>

<script setup lang="ts">
interface Props {
  userId: string
}
const props = defineProps<Props>()
let newUser = {
  name: '',
  date: '',
  surname: '',
  role: ''
}

JSON.parse(localStorage.getItem('users') as string).filter((elem: any, index: any) => {
  if (elem.userId === Number(props.userId)) {
    newUser = JSON.parse(localStorage.getItem('users') as string)[index]
    localStorage.removeItem('index')
    localStorage.setItem('index', index)
  }
})
const user = JSON.parse(localStorage.getItem('users') as string)
console.log(newUser)

const editLocalStorage = (e: any) => {
  e.preventDefault()
  user[localStorage.getItem('index') as string] = {
    ...newUser
  }

  localStorage.setItem('users', JSON.stringify(user))
  // window.location.reload()
}
</script>

<style scoped>
.returnBack {
  display: block;
  margin-left: 0px;
  margin-bottom: 10px;
}
.editPage {
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: max-content;
}
a {
  width: max-content;
  margin: 0 auto;
  margin-top: 20px;
  padding: 10px 20px;
  background-color: gray;
  color: white;
  border: none;
  text-decoration: none;
  border-radius: 20px;
  cursor: pointer;
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
  background-color: brown;
  transition: all 3s ease;
}
.link:hover::after {
  width: 100%;
}
</style>
