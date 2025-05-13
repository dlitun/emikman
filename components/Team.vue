<template>
  <section class="container">
    <div class="team-section">
      <div class="team-header">
        <div class="text">
          <h2>Наша команда</h2>
          <p>
            Каждый участник команды вносит вклад в высокое качество решений, сохраняет
            приверженность ответственности и эффективности, объединяя это с лучшими
            практиками дизайна.
          </p>
        </div>
        <div class="buttons">
          <button @click="swiper?.slidePrev()">Назад</button>
          <button @click="swiper?.slideNext()">Вперед</button>
        </div>
      </div>
  
      <Swiper
        class="team-swiper"
        :slides-per-view="'auto'"
        :space-between="20"
        @swiper="onSwiper"
      >
        <SwiperSlide v-for="(member, index) in team" :key="index" class="team-slide">
          <div class="card">
            <img :src="member.photo" alt="Фото" />
            <h3>{{ member.name }}</h3>
            <p>{{ member.role }}</p>
          </div>
        </SwiperSlide>
      </Swiper>
    </div>
  </section>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import { Swiper, SwiperSlide } from 'swiper/vue'
  import 'swiper/css'
  
  const swiper = ref(null)
  const onSwiper = (s) => {
    swiper.value = s
  }
  
  const team = [
    { name: 'Иван Петров', role: 'UX дизайнер', photo: '/_nuxt/assets/src/team/1.png' },
    { name: 'Ольга Иванова', role: 'UI дизайнер', photo: '/_nuxt/assets/src/team/2.png' },
    { name: 'Алексей Смирнов', role: 'Frontend разработчик', photo: '/_nuxt/assets/src/team/3.png' },
    { name: 'Мария Кузнецова', role: 'Product менеджер', photo: '/_nuxt/assets/src/team/4.png' },
    { name: 'Дмитрий Волков', role: 'Аналитик', photo: '/_nuxt/assets/src/team/5.png' },
    { name: 'Елена Соколова', role: 'Backend разработчик', photo: '/_nuxt/assets/src/team/6.png' },
    { name: 'Никита Орлов', role: 'QA инженер', photo: '/_nuxt/assets/src/team/7.png' },
    { name: 'Анна Белова', role: 'Project менеджер', photo: '/_nuxt/assets/src/team/8.png' },
  ]
  </script>
  
  <style scoped>
  .team-section {
    padding: 40px 0;
    overflow: hidden;
  }
  
  .team-header {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 30px;
    gap: 20px;
    flex-wrap: wrap;
  }
  
  .team-header .text {
    max-width: 600px;
  }
  
  .team-header h2 {
    font-size: 32px;
    margin-bottom: 10px;
  }
  
  .team-header p {
    font-size: 18px;
    line-height: 1.5;
  }
  
  .team-header .buttons {
    display: flex;
    gap: 10px;
  }
  
  .team-header .buttons button {
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
  }
  
  /*.team-swiper {
    padding-left: 5vw;
    padding-right: 5vw;
  }*/
  
  .team-slide {
    width: 260px;
    flex-shrink: 0;
  }
  
  .card {
    background: white;
    border-radius: 12px;
    padding: 20px;
    text-align: center;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  }
  
  .card img {
    width: 100%;
    border-radius: 8px;
    margin-bottom: 15px;
  }
  
  .card h3 {
    margin: 0 0 5px;
    font-size: 18px;
  }
  
  .card p {
    margin: 0;
    font-size: 14px;
    color: #666;
  }
  </style>
  