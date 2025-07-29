<script setup>
import WorkItem from './components/WorkItem.vue'
</script>

<template>
  <header style="height: 3rem; justify-content: space-between" class="d-flex">
    <div></div>
    <div style="gap: 0.25rem" class="d-flex">
      <a>
        <img src="./assets/icons/outline.png" />
      </a>
    </div>
  </header>
  <main class="w-100">
    <div style="margin-top: 3rem" class="d-flex flex-column align-items-center">
      <div class="w-50 d-flex flex-column">
        <h1 class="mb-2">Devin Broussard</h1>
        <div class="prose">
          <p>
            Hi! I'm Devin, a full-stack software engineer and arch linux/open source enthusiast.
          </p>
          <p>Working at <a href="https://www.bamtech.net" target="_blank">Bam Technologies</a></p>
          <p>
            Outside of programming, I enjoy doing photography and traveling. I post photos on this
            page. I also love anime, movies and dramas, I am trying to list my media consumption.
            Also, in case you are interested, here are the hardware/software I use.
          </p>
        </div>
        <h2>Work</h2>
        <WorkItem
          title="BAM Technologies"
          description="Currently working full time on Nord Design System. We use modern technologies such as Web Components and CSS Custom Properties to provide the wider design and development team everything they need to design and build products such as Provet Cloud, Diarium, Navisec Health and many more."
          imgPath="../assets/icons/BAM-technologies.jpg"
        ></WorkItem>
        <WorkItem
          title="Veris Global"
          description="Currently working full time on Nord Design System. We use modern technologies such as Web Components and CSS Custom Properties to provide the wider design and development team everything they need to design and build products such as Provet Cloud, Diarium, Navisec Health and many more."
          imgPath="../assets/icons/WhiteVerisIcon.png"
          :isLastItem="true"
        ></WorkItem>
      </div>
    </div>
  </main>
</template>

<style scoped>
h1 {
  color: var(--color-heading);
  font-size: 36px;
  font-weight: 450;
}

h2 {
  color: var(--color-heading);
}

.html {
  font-family: 'Inter', sans-serif;
  font-optical-sizing: auto;
  font-style: normal;
  font-size: 16px;
}

.mb-header {
  margin-bottom: 7rem;
}

.mb-1 {
  margin-bottom: 0.25rem;
}

.mb-5 {
  margin-bottom: 2rem;
}

.mb-2 {
  margin-bottom: 0.5rem;
}

.mb-3 {
  margin-bottom: 1rem;
}

.mt-5 {
  margin-top: 2rem;
}

.w-100 {
  width: 100%;
}

.w-75 {
  width: 75%;
}

.w-50 {
  width: 50%;
}

.justify-content-center {
  justify-content: center;
}

.d-flex {
  display: flex;
}

.flex-column {
  flex-direction: column;
}

.align-items-center {
  align-items: center;
}

.prose {
  p {
    margin-top: 1.25rem;
    margin-bottom: 1.25rem;
  }
}
</style>
