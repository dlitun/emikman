<template>
  <section class="container-full hero">
    <video autoplay muted loop playsinline class="hero-video">
      <source src="/assets/src/banner.mp4" type="video/mp4" />
      Ваш браузер не поддерживает видео.
    </video>

    <div class="overlay"></div>

    <div class="hero-content">
      <h1>Создаем цифровые решения<br/>для комфортной жизни </h1>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  color: white;
  text-align: center;
}

.hero-video {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -2;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5); /* полупрозрачное затемнение */
  z-index: -1;
}

.hero-content {
  position: relative;
  z-index: 1;
  padding: 20px;
}

.hero-content h1 {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.hero-content p {
  font-size: 1.5rem;
}

@media (max-width: 768px) {
  .hero-content h1 {
    font-size: 2rem;
  }

  .hero-content p {
    font-size: 1rem;
  }
}
</style>
