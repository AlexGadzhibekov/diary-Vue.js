<template>
  <div class="addLesson">
    <router-link class="link" :to="{ name: 'LessonsAdd' }">Добавить новое занятие</router-link>
  </div>
  <h2>Список Занятий</h2>
  <div class="cards">
    <lesson-list v-for="lesson in lessons" :lesson="lesson" :key="lesson.lessonId"></lesson-list>
  </div>
</template>

<script setup lang="ts">
import LessonList from '@/components/LessonList.vue'
const lessons = JSON.parse(localStorage.getItem('lessons'))
</script>

<style scoped>
.addLesson {
  position: absolute;
  top: 30px;
  right: 140px;
}
.addLesson a {
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
</style>
