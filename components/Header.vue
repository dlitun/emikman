<template>
  <header class="header">
    <div class="container">
      <div class="header__inner">
        <!-- Логотип -->
        <div class="logo">
          <img src="/assets/src/logo.svg" alt="Логотип" class="logo__img" />
        </div>

        <!-- Единое меню -->
        <nav class="menu" :class="{ 'is-open': isMenuOpen }">
          <ul class="menu__list">
            <li class="menu__item">
              <a href="#projects" class="menu__link" @click="toggleMenu">Проекты</a>
            </li>
            <li class="menu__item">
              <a href="#about" class="menu__link" @click="toggleMenu">О нас</a>
            </li>
            <li class="menu__item">
              <a href="#services" class="menu__link" @click="toggleMenu">Услуги</a>
            </li>
            <li class="menu__item">
              <a href="#team" class="menu__link" @click="toggleMenu">Команда</a>
            </li>
            <li class="menu__item">
              <a href="#contacts" class="menu__link" @click="toggleMenu">Контакты</a>
            </li>
          </ul>
          <div class="menu__buttons">
            <button class="btn">Презентация</button>
            <button class="btn">Обсудить проект</button>
          </div>
        </nav>

        <!-- Кнопка гамбургера -->
        <button class="hamburger" :class="{ 'is-active': isMenuOpen }" @click="toggleMenu" aria-label="Переключить меню">
          <span></span>
          <span></span>
          <span></span>
        </button>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      isMenuOpen: false,
    };
  },
  methods: {
    toggleMenu() {
      if (window.innerWidth <= 768) {
        this.isMenuOpen = !this.isMenuOpen;
        document.body.style.overflow = this.isMenuOpen ? 'hidden' : '';
      }
    },
    handleResize() {
      if (window.innerWidth > 768 && this.isMenuOpen) {
        this.isMenuOpen = false;
        document.body.style.overflow = '';
      }
    },
  },
  mounted() {
    window.addEventListener('resize', this.handleResize);
    this.handleResize(); // Проверка при монтировании
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.handleResize);
  },
};
</script>

<style scoped>

.container {
  max-width: 1600px;
  margin: 0 auto;
  padding: 0 15px;
}

.header {
  padding: 20px 0;
  background-color: var(--color-white);
  position: fixed;
  z-index: 1000;
  width: 100%;
  border-bottom: 1px solid hsla(0, 0%, 100%, .1);
  box-shadow: 0 1.2rem 2rem #0000000d;
}

.header__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo__img {
  height: 32px;
  display: block;
}

.menu {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.menu__list {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
}

.menu__item {
  margin: 0 15px;
}

.menu__link {
  text-decoration: none;
  color: #333;
  font-size: 16px;
  transition: color 0.3s;
}

.menu__link:hover {
  color: #007bff;
}

.menu__buttons {
  display: flex;
  gap: 10px;
}

.hamburger {
  display: none;
  flex-direction: column;
  justify-content: space-between;
  width: 30px;
  height: 20px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
  z-index: 1001;
  order: 3; /* Гарантирует позицию справа в flex */
}

.hamburger span {
  display: block;
  width: 100%;
  height: 3px;
  background: #333;
  transition: all 0.3s ease;
}

.hamburger.is-active span:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}

.hamburger.is-active span:nth-child(2) {
  opacity: 0;
}

.hamburger.is-active span:nth-child(3) {
  transform: rotate(-45deg) translate(7px, -7px);
}

@media (max-width: 768px) {
  .menu {
    position: fixed;
    top: 90px;
    left: 0;
    width: 100%;
    height: calc(100% - 90px);
    background: #fff;
    z-index: 999;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    transform: translateX(100%);
    transition: transform 0.3s ease-in-out;
  }

  .menu.is-open {
    transform: translateX(0);
  }

  .menu__list {
    flex-direction: column;
    align-items: center;
    margin: 40px 0;
  }

  .menu__item {
    margin: 20px 0;
  }

  .menu__link {
    font-size: 24px;
  }

  .menu__buttons {
    flex-direction: column;
    gap: 20px;
  }

  .hamburger {
    display: flex;
  }

  /* Логотип виден на мобильных, но перемещается в меню при открытии */
  .menu.is-open .logo {
    position: absolute;
    top: 20px;
    left: 50%;
    transform: translateX(-50%);
  }
}

@media (min-width: 769px) {
  .menu {
    display: flex !important;
  }

  .logo {
    display: block;
  }

  .menu__buttons {
    display: flex !important;
  }

  .hamburger {
    display: none !important;
  }
}
</style>