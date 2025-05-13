```vue
<template>
  <section id="client-list" class="client-list container-full">
    <!-- Контейнер для слайдера -->
    <div class="rfm-marquee-container">
      <div class="rfm-marquee">
        <div class="rfm-child-container">
          <!-- Первый ряд с логотипами (движется слева направо) -->
          <div class="rfm-child left-to-right">
            <div class="client-item" v-for="(client, index) in clientsRow1" :key="index">
              <img :src="client.src" :alt="client.alt" :width="client.width" :height="client.height" loading="lazy" />
            </div>
            <!-- Дублируем содержимое для бесшовного эффекта -->
            <div class="client-item" v-for="(client, index) in clientsRow1" :key="'dup1-' + index">
              <img :src="client.src" :alt="client.alt" :width="client.width" :height="client.height" loading="lazy" />
            </div>
          </div>

          <!-- Второй ряд с логотипами (движется справа налево) -->
          <div class="rfm-child right-to-left">
            <div class="client-item" v-for="(client, index) in clientsRow2" :key="'second-' + index">
              <img :src="client.src" :alt="client.alt" :width="client.width" :height="client.height" loading="lazy" />
            </div>
            <!-- Дублируем содержимое для бесшовного эффекта -->
            <div class="client-item" v-for="(client, index) in clientsRow2" :key="'dup2-' + index">
              <img :src="client.src" :alt="client.alt" :width="client.width" :height="client.height" loading="lazy" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      // Логотипы для первого ряда
      clientsRow1: [
        { src: '/assets/src/clients/mtc.svg', alt: 'MTC', width: 131, height: 130 },
        { src: '/_nuxt/assets/src/clients/sber.svg', alt: 'Sber', width: 273, height: 74 },
        { src: '/_nuxt/assets/src/clients/tele2.svg', alt: 'Tele2', width: 196, height: 74 },
        { src: '/_nuxt/assets/src/clients/gaz.svg', alt: 'Gaz', width: 71, height: 80 },
        { src: '/_nuxt/assets/src/clients/pepsi.svg', alt: 'Pepsi', width: 195, height: 74 },
        { src: '/_nuxt/assets/src/clients/mir.svg', alt: 'Mir', width: 155, height: 44 },
        { src: '/_nuxt/assets/src/clients/hyundai.svg', alt: 'Hyundai', width: 401, height: 52 },
        { src: '/_nuxt/assets/src/clients/purina.svg', alt: 'Purina', width: 329, height: 58 }
      ],
      // Логотипы для второго ряда
      clientsRow2: [
        { src: '/_nuxt/assets/src/clients/vtb.svg', alt: 'VTB', width: 187, height: 66 },
        { src: '/_nuxt/assets/src/clients/mastercard.svg', alt: 'Mastercard', width: 120, height: 74 },
        { src: '/_nuxt/assets/src/clients/ozon.svg', alt: 'Ozon', width: 210, height: 46 },
        { src: '/_nuxt/assets/src/clients/visa.svg', alt: 'Visa', width: 154, height: 50 },
        { src: '/_nuxt/assets/src/clients/yandex.svg', alt: 'Yandex', width: 212, height: 62 },
        { src: '/_nuxt/assets/src/clients/mtc.svg', alt: 'MTC', width: 131, height: 130 },
        { src: '/_nuxt/assets/src/clients/sber.svg', alt: 'Sber', width: 273, height: 74 }
      ]
    };
  }
};
</script>

<style scoped>
.client-list {
  width: 100%;
  overflow: hidden;
}

.rfm-marquee-container {
  display: flex;
  overflow: hidden;
  width: 100%;
}

.rfm-marquee {
  display: flex;
  flex-direction: column;
}

.rfm-child-container {
  display: flex;
  flex-wrap: nowrap;
  flex-direction: column;
}

.rfm-child {
  display: flex;
  flex-direction: row;
  width: max-content; /* Устанавливаем ширину по содержимому */
}

.left-to-right {
  animation: left-to-right 30s linear infinite;
}

.right-to-left {
  animation: right-to-left 30s linear infinite;
}

.client-item {
  margin-right: 20px;
  flex: 0 0 auto; /* Запрещаем сжатие элементов */
}

.client-item img {
  max-width: 100%;
  height: auto;
}

@keyframes left-to-right {
  0% {
    transform: translateX(-50%); /* Начинаем с половины дублированного содержимого */
  }
  100% {
    transform: translateX(0); /* Движение слева направо */
  }
}

@keyframes right-to-left {
  0% {
    transform: translateX(0); /* Начинаем с правого края */
  }
  100% {
    transform: translateX(-50%); /* Движение справа налево */
  }
}
</style>
```
