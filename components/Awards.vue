<template>
  <section class="container">
      <h2>Награды и достижения</h2>
      
      <div class="blocks">
      <div
        v-for="(block, index) in blocks"
        :key="index"
        :class="['block', `block-${index + 1}`]"
        :data-gradient="block.gradient"
        ref="blockRefs"
      >
        <canvas></canvas>
        <div class="content">
          <h2>{{ block.title }}</h2>
          <p>{{ block.description }}</p>
        </div>
      </div>
    </div>
  </section>
  </template>
  
  <script setup>
  import { onMounted, ref, nextTick } from 'vue'
  
  const blocks = [
    { title: 'CDO/CDTO Awards 2024', description: 'Проект «Рексофт» для ГК «Современные транспортные технологии» назван лучшим в номинации «Digital-проект года» в ИТ-сфере на «CDO/CDTO Awards 2024»', gradient: '0,255,255' },
    { title: 'Retail Week Awards 2023', description: 'Победа в номинации «HR-решение года» — продукт Sales KPI. Вместе с командой в М.Тех создав продукт, который увеличивает прибыль компаний благодаря высокой вовлеченности сотрудников и интеграции с другими продуктами, включая чат-бот и Verme', gradient: '255,0,0' },
    { title: 'POPAI AWARDS 2018', description: 'Вместе с командой «Инициум», которая развивает сеть терминалов интерактивной навигации Directorix™, заняла первое место в Международном конкурсе POPAI AWARDS в номинации Digital Media за проект интерактивных терминалов парка «Зарядье»', gradient: '0,255,0' },
    { title: 'HR Tech Award «Цифровая пирамида – 2023»', description: 'Гран-при за совместный проект М.Видео-Эльдорадо и Verme «Биржа смен»', gradient: '255,255,0' },

  ]
  
  const blockRefs = ref([])
  
  onMounted(async () => {
    await nextTick()
    blockRefs.value.forEach((blockEl, index) => {
      const canvas = blockEl.querySelector('canvas')
      const ctx = canvas.getContext('2d')
      const rgb = blockEl.dataset.gradient.split(',').map(Number)
  
      let opacity = 0
      let targetOpacity = 0
      let lastX = 0
      let lastY = 0
  
      function resizeCanvas() {
        canvas.width = blockEl.offsetWidth
        canvas.height = blockEl.offsetHeight
      }
      resizeCanvas()
      window.addEventListener('resize', resizeCanvas)
  
      function drawGradient(x, y, currentOpacity) {
        ctx.clearRect(0, 0, canvas.width, canvas.height)
        const gradient = ctx.createRadialGradient(x, y, 0, x, y, Math.max(canvas.width, canvas.height) / 3)
        gradient.addColorStop(0, `rgba(${rgb[0]},${rgb[1]},${rgb[2]},${currentOpacity})`)
        gradient.addColorStop(1, 'transparent')
        ctx.fillStyle = gradient
        ctx.fillRect(0, 0, canvas.width, canvas.height)
      }
  
      function animateOpacity() {
        if (Math.abs(opacity - targetOpacity) > 0.01) {
          opacity += (targetOpacity - opacity) * 0.1
          drawGradient(lastX, lastY, opacity)
          requestAnimationFrame(animateOpacity)
        } else {
          opacity = targetOpacity
          if (opacity === 0) {
            ctx.clearRect(0, 0, canvas.width, canvas.height)
          } else {
            drawGradient(lastX, lastY, opacity)
          }
        }
      }
  
      blockEl.addEventListener('mouseenter', () => {
        targetOpacity = 0.7
        animateOpacity()
      })
      blockEl.addEventListener('mousemove', (e) => {
        const rect = canvas.getBoundingClientRect()
        lastX = e.clientX - rect.left
        lastY = e.clientY - rect.top
        drawGradient(lastX, lastY, opacity)
      })
      blockEl.addEventListener('mouseleave', () => {
        targetOpacity = 0
        animateOpacity()
      })
    })
  })
  </script>
  
  <style scoped>
  body {
    margin: 0;
  }
  .container {
    display: flex;
    flex-wrap: wrap;

    justify-content: space-between;
    max-width: 1600px;
    margin: 0 auto;

  }
  .block {
    position: relative;
    height: 300px;
    flex: 0 1 25%;
    min-width: 200px;
    border-radius: 10px;
    overflow: hidden;
    background-color: white;
  }

  .blocks {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 16px;
}

  .block-1, .block-4 { flex: 0 1 35%; }
  .block-2, .block-3 { flex: 0 1 55%; }
  canvas {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 2;

  }
  .content {
    position: relative;
    z-index: 3;
    padding: 20px;
    color: black;
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
  .block-1, .block-4 { flex: 0 1 100%; }
  .block-2, .block-3 { flex: 0 1 100%; }
  }
  @media (max-width: 480px) {
    .block {
      flex: 0 1 100%;
    }
  }
  </style>
  