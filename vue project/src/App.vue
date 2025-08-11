<script setup>
import WorkItem from './components/WorkItem.vue'
import { onMounted, ref } from 'vue'

const isDarkTheme = ref(false)

const getSystemPreference = () => {
  return window.matchMedia('(prefers-color-scheme: dark)').matches
}

const toggleTheme = () => {
  isDarkTheme.value = !isDarkTheme.value
  updateThemeClass()
  saveThemPreference()
}

const updateThemeClass = () => {
  const body = document.body
  body.classList.remove('theme-dark')

  if (isDarkTheme.value) {
    body.classList.add('theme-dark')
  }
}

const saveThemPreference = () => {
  localStorage.setItem('theme', isDarkTheme.value ? 'dark' : 'light')
}

onMounted(() => {
  const savedTheme = localStorage.getItem('theme')

  if (savedTheme) {
    isDarkTheme.value = savedTheme === 'dark'
  } else {
    isDarkTheme.value = getSystemPreference()
  }

  updateThemeClass()
})
</script>

<template>
  <header class="header">
    <p>Work</p>
    <p>Projects</p>
    <a class="icon-link" href="https://github.com/devinbroussard" target="_blank">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        data-name="Layer 1"
        viewBox="0 0 24 24"
        id="github-alt"
      >
        <path
          fill="currentcolor"
          d="M10.07031,20.50291a1.00008,1.00008,0,0,0-1.18115-.9834c-1.30908.24024-2.96191.27637-3.40137-.958a5.70754,5.70754,0,0,0-1.83691-2.415,1.20073,1.20073,0,0,1-.1665-.10938,1,1,0,0,0-.93067-.64551H2.54883a.99965.99965,0,0,0-1,.99512c-.00391.81543.811,1.33789,1.1416,1.51465a4.4408,4.4408,0,0,1,.92383,1.35937c.36426,1.02344,1.42285,2.57617,4.46582,2.376.001.03516.00195.06836.00244.09863l.00439.26758a1,1,0,0,0,2,0l-.00488-.31836C10.07715,21.4951,10.07031,21.22068,10.07031,20.50291Zm10.667-15.126c.03174-.125.063-.26367.09034-.41992a6.27792,6.27792,0,0,0-.40821-3.293,1.002,1.002,0,0,0-.61572-.58007c-.356-.12012-1.67041-.35645-4.18408,1.25a13.86918,13.86918,0,0,0-6.354,0C6.76221.751,5.45459.9658,5.10205,1.07908a.99744.99744,0,0,0-.63135.584,6.3003,6.3003,0,0,0-.40332,3.35644c.02442.12793.05078.2461.07813.35449A6.26928,6.26928,0,0,0,2.89014,9.20311a8.42168,8.42168,0,0,0,.04248.92187c.334,4.60254,3.334,5.98438,5.42431,6.459-.04345.125-.083.25878-.11816.40039a1.00023,1.00023,0,0,0,1.94238.47851,1.6784,1.6784,0,0,1,.46778-.87793.99947.99947,0,0,0-.5459-1.74512c-3.4541-.39453-4.95362-1.80175-5.1792-4.89843a6.61076,6.61076,0,0,1-.03369-.73828,4.25769,4.25769,0,0,1,.91943-2.71289,3.022,3.022,0,0,1,.1958-.23145.99988.99988,0,0,0,.188-1.02441,3.3876,3.3876,0,0,1-.15527-.55567A4.09356,4.09356,0,0,1,6.1167,3.06346a7.54263,7.54263,0,0,1,2.415,1.17968,1.00877,1.00877,0,0,0,.82764.13282,11.77716,11.77716,0,0,1,6.17285.001,1.00549,1.00549,0,0,0,.83056-.13769,7.572,7.572,0,0,1,2.40528-1.19043,4.03977,4.03977,0,0,1,.0874,1.57812,3.205,3.205,0,0,1-.16895.60743.9999.9999,0,0,0,.188,1.02441c.07715.08691.1543.18066.22363.26855A4.12186,4.12186,0,0,1,20,9.20311a7.03888,7.03888,0,0,1-.0376.77734c-.22021,3.05566-1.72558,4.46387-5.1958,4.85937a1,1,0,0,0-.54541,1.7461,1.63079,1.63079,0,0,1,.46631.9082,3.06079,3.06079,0,0,1,.09229.81934v2.334C14.77,21.2949,14.77,21.78025,14.77,22.00291a1,1,0,1,0,2,0c0-.2168,0-.69238.00977-1.33984V18.31346a4.8815,4.8815,0,0,0-.15479-1.31153,4.25638,4.25638,0,0,0-.11621-.416,6.51258,6.51258,0,0,0,5.44531-6.42383A8.69677,8.69677,0,0,0,22,9.20311,6.13062,6.13062,0,0,0,20.7373,5.37693Z"
        ></path>
      </svg>
    </a>
    <a class="icon-link" href="https://www.linkedin.com/in/devinraybroussard/" target="_blank">
      <svg xmlns="http://www.w3.org/2000/svg" data-name="Layer 1" viewBox="0 0 24 24" id="linkedin">
        <path
          fill="currentcolor"
          d="M20.47,2H3.53A1.45,1.45,0,0,0,2.06,3.43V20.57A1.45,1.45,0,0,0,3.53,22H20.47a1.45,1.45,0,0,0,1.47-1.43V3.43A1.45,1.45,0,0,0,20.47,2ZM8.09,18.74h-3v-9h3ZM6.59,8.48h0a1.56,1.56,0,1,1,0-3.12,1.57,1.57,0,1,1,0,3.12ZM18.91,18.74h-3V13.91c0-1.21-.43-2-1.52-2A1.65,1.65,0,0,0,12.85,13a2,2,0,0,0-.1.73v5h-3s0-8.18,0-9h3V11A3,3,0,0,1,15.46,9.5c2,0,3.45,1.29,3.45,4.06Z"
        ></path>
      </svg>
    </a>
    <button class="icon-button" v-if="isDarkTheme" @click="toggleTheme">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" id="sun">
        <path
          fill="currentcolor"
          d="M5.64,17l-.71.71a1,1,0,0,0,0,1.41,1,1,0,0,0,1.41,0l.71-.71A1,1,0,0,0,5.64,17ZM5,12a1,1,0,0,0-1-1H3a1,1,0,0,0,0,2H4A1,1,0,0,0,5,12Zm7-7a1,1,0,0,0,1-1V3a1,1,0,0,0-2,0V4A1,1,0,0,0,12,5ZM5.64,7.05a1,1,0,0,0,.7.29,1,1,0,0,0,.71-.29,1,1,0,0,0,0-1.41l-.71-.71A1,1,0,0,0,4.93,6.34Zm12,.29a1,1,0,0,0,.7-.29l.71-.71a1,1,0,1,0-1.41-1.41L17,5.64a1,1,0,0,0,0,1.41A1,1,0,0,0,17.66,7.34ZM21,11H20a1,1,0,0,0,0,2h1a1,1,0,0,0,0-2Zm-9,8a1,1,0,0,0-1,1v1a1,1,0,0,0,2,0V20A1,1,0,0,0,12,19ZM18.36,17A1,1,0,0,0,17,18.36l.71.71a1,1,0,0,0,1.41,0,1,1,0,0,0,0-1.41ZM12,6.5A5.5,5.5,0,1,0,17.5,12,5.51,5.51,0,0,0,12,6.5Zm0,9A3.5,3.5,0,1,1,15.5,12,3.5,3.5,0,0,1,12,15.5Z"
        ></path>
      </svg>
    </button>
    <button class="icon-button" v-if="!isDarkTheme" @click="toggleTheme">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" id="moon">
        <path
          fill="currentcolor"
          d="M21.64,13a1,1,0,0,0-1.05-.14,8.05,8.05,0,0,1-3.37.73A8.15,8.15,0,0,1,9.08,5.49a8.59,8.59,0,0,1,.25-2A1,1,0,0,0,8,2.36,10.14,10.14,0,1,0,22,14.05,1,1,0,0,0,21.64,13Zm-9.5,6.69A8.14,8.14,0,0,1,7.08,5.22v.27A10.15,10.15,0,0,0,17.22,15.63a9.79,9.79,0,0,0,2.1-.22A8.11,8.11,0,0,1,12.14,19.73Z"
        ></path>
      </svg>
    </button>
  </header>
  <main class="w-100">
    <div style="margin-top: 4rem" class="d-flex flex-column align-items-center">
      <div class="d-flex flex-column" style="width: 40rem">
        <h1>Devin Broussard</h1>
        <div class="prose">
          <p>
            Hi! I'm Devin, a full-stack software engineer and arch linux/open source enthusiast
            currently working at
            <a href="https://www.bamtech.net" target="_blank">Bam Technologies</a>.
          </p>
          <p>
            Outside of programming, I enjoy doing photography and traveling. I post photos on this
            page. I also love anime, movies and dramas, I am trying to list my media consumption.
            Also, in case you are interested, here are the hardware/software I use.
          </p>
        </div>
        <!-- <h2>Work</h2>
        <WorkItem
          title="BAM Technologies"
          description="Currently working full time on Nord Design System. We use modern technologies such as Web Components and CSS Custom Properties to provide the wider design and development team everything they need to design and build products such as Provet Cloud, Diarium, Navisec Health and many more."
          imgPath="../assets/icons/BAM-technologies.jpg"
          isFullSizeIcon="true"
        ></WorkItem>
        <WorkItem
          title="Veris Global"
          description="Currently working full time on Nord Design System. We use modern technologies such as Web Components and CSS Custom Properties to provide the wider design and development team everything they need to design and build products such as Provet Cloud, Diarium, Navisec Health and many more."
          imgPath="../assets/icons/WhiteVerisIcon.png"
          :isLastItem="true"
        ></WorkItem> -->
      </div>
    </div>
  </main>
</template>

<style scoped>
.icon-button {
  border: none;
  padding: 0px;
  background-color: unset;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 20px;
  width: 20px;
  color: var(--color-text);
  cursor: pointer;
}

.icon-link {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 20px;
  width: 20px;
  color: var(--color-text);
}

.header-icon {
  height: 20px;
  width: 20px;
  filter: invert(0.8);
}

.header {
  height: 3rem;
  display: flex;
  justify-content: end;
  align-items: center;
  gap: 1.2rem;
  width: 100%;
  padding-left: 2rem;
  padding-right: 2rem;
  padding-top: 2rem;
}

h1 {
  color: var(--color-heading);
  font-size: 40px;
  font-weight: 500;
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
    margin-top: 1.2rem;
    margin-bottom: 1.2rem;
  }
}
</style>
