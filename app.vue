<template>
  <div>
    <Header />
    <main>
        <Hero />
        <Portfolio />
        <About />
        <Clients />
        <Services />
        <Team />
        <Awards />
        <Contact />
    </main>
    <Footer />
  </div>
</template>

<script setup>
useHead({
  link: [
    {
      rel: 'stylesheet',
      href: 'https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap'
    }
  ]
})
</script>
