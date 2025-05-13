<template>
  <section class="container">
  <div>
    <div class="text">
          <h2>Наши ключевые направления</h2>
          <p>
            Оказываем качественные услуги, которые помогут вам достичь поставленных целей
          </p>
        </div>
    <div
      v-for="(service, index) in services"
      :key="index"
      :class="['block', `block-${index + 1}`]"
    >
      <div :class="['content', `content-${index + 1}`]">
        <h2>{{ service.title }}</h2>
        <p>{{ service.description }}</p>
      </div>
    </div>
  </div>
  </section>
</template>

<script setup>
const services = [
  {
    title: 'Инфраструктура',
    description:
      'Решаем цифровые продукты и сервисы, которые делают жизнь сотрудников, водителей и посетителей зданий проще и комфортнее.',
  },
  {
    title: 'Ритейл',
    description:
      'Разрабатываем интерфейсы для увеличения продаж и улучшения клиентского опыта.',
  },
  {
    title: 'Мероприятия',
    description:
      'Проектируем для различных форматов, делая взаимодействие участников простым и удобным.',
  },
  {
    title: 'Телеком',
    description:
      'Работаем над улучшением связи через современные и доступные продукты.',
  },
  {
    title: 'Транспорт и логистика',
    description:
      'Создаем решения для эффективного управления транспортом и оптимизируем процессы доставки.',
  },
  {
    title: 'Сырье',
    description:
      'Разрабатываем инструменты для анализа данных и статистики, упрощающие работу с сырьем и производственными процессами.',
  },
  {
    title: 'Игровая индустрия',
    description:
      'Делаем игровые интерфейсы захватывающими и простыми в использовании, повышая вовлеченность игроков.',
  },
  {
    title: 'Финтех',
    description:
      'Делаем сервисы понятными и надежными, обеспечивая безопасность и удобство для пользователей.',
  },
  {
    title: 'Другие',
    description:
      'Облегчаем выполнение повседневных задач, освобождая время для важных стратегических решений.',
  },
]
</script>

<style scoped>
/* вместо section.services */
div {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: space-between;
  padding: 20px;
}

.block {
  position: relative;
  height: 300px;
  flex: 1 1 25%;
  min-width: 200px;
  border-radius: 10px;
  overflow: hidden;
  background-color: white;
}

.block-1,
.block-4,
.block-7 {
  flex: 1 1 25%;
}
.block-2,
.block-5,
.block-8 {
  flex: 1 1 50%;
}
.block-3,
.block-6,
.block-9 {
  flex: 1 1 25%;
}

.content {
  position: relative;
  z-index: 1;
  color: black;
  height: 100%;
  box-sizing: border-box;
  background-size: 250px 250px;
  background-repeat: no-repeat;
  background-position: bottom right;
}

.content-1 {
  background-image: url('/assets/src/services/1.png');
}
.content-2 {
  background-image: url('/assets/src/services/2.png');
}
.content-3 {
  background-image: url('/assets/src/services/3.png');
}
.content-4 {
  background-image: url('/assets/src/services/4.png');
}
.content-5 {
  background-image: url('/assets/src/services/5.png');
}
.content-6 {
  background-image: url('/assets/src/services/6.png');
}
.content-7 {
  background-image: url('/assets/src/services/7.png');
}
.content-8 {
  background-image: url('/assets/src/services/8.png');
}
.content-9 {
  background-image: url('/assets/src/services/9.png');
}

.content h2 {
  font-size: 24px;
  margin: 0 0 10px;
}

.content p {
  font-size: 16px;
  margin: 0;
}

@media (max-width: 768px) {
  .block-1,
  .block-4,
  .block-7 {
    flex: 0 1 100%;
  }
  .block-2,
  .block-5,
  .block-8 {
    flex: 0 1 100%;
  }
  .block-3,
  .block-6,
  .block-9 {
    flex: 0 1 100%;
  }
}

@media (max-width: 480px) {
  .block {
    flex: 0 1 100%;
  }
}
</style>
