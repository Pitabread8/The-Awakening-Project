<script setup>
useHead({
  script: [{ src: "https://unpkg.com/aos@next/dist/aos.js", body: true }],
});
</script>

<script>
import prelude from "../assets/audio/prelude.mp3";
import milliondollarman from "../assets/audio/milliondollarman.mp3";
import poetpeasant from "../assets/audio/poetpeasant.mp3";
import ride from "../assets/audio/ride.mp3";
import fadeintoyou from "../assets/audio/fadeintoyou.mp3";
import lookbridge from "../assets/audio/lookbridge.mp3";
import zampa from "../assets/audio/zampa.mp3";
import seabirds from "../assets/audio/seabirds.ogg";

export default {
  beforeMount() {
    window.addEventListener("scroll", this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener("scroll", this.handleScroll);
    this.audio.pause();
  },
  data() {
    return {
      isOpen: false,
      a: 0,
      audio: new Audio(prelude),
    };
  },
  methods: {
    handleScroll() {
      let sections = document.getElementsByTagName("section");
      let positions = [];
      for (let s = 0; s < sections.length; s++) {
        positions.push(sections[s].offsetTop);
      }

      let scroll = window.scrollY + window.innerHeight / 2;
      let closest = positions.reverse().find((e) => e <= scroll);
      positions.reverse();

      let index = positions.indexOf(closest);

      let numerals = ["0", "I", "II", "III", "IV", "V", "VI", "VII"];
      document.getElementById("number").innerText = numerals[index];

      let audios = [prelude, milliondollarman, zampa, ride, fadeintoyou, lookbridge, poetpeasant, seabirds];

      if (index != this.a) {
        this.audio.pause();
        this.audio = new Audio(audios[index]);
        this.audio.play();
        this.a = index;
      }
    },
    openPage() {
      this.isOpen = true;
      this.audio.play();
      AOS.init();
    },
  },
};
</script>

<template>
  <Head>
    <Link rel="stylesheet" href="https://unpkg.com/aos@next/dist/aos.css" />
  </Head>
  <div v-if="!isOpen" class="fixed left-0 top-0 h-screen w-screen bg-blue-100">
    <button id="open" @click="openPage()" class="fixed left-1/2 top-1/2 h-36 w-36 translate-x-[-50%] translate-y-[-50%] rounded-full bg-blue-950 text-8xl">
      <Icon class="absolute left-1/2 top-1/2 translate-x-[-50%] translate-y-[-50%] text-blue-100" name="mdi:play" />
    </button>
  </div>
  <div v-if="isOpen" class="fixed right-[3%] top-1/2 h-36 w-36 translate-y-[-50%] rounded-full bg-blue-950">
    <p id="number" class="absolute left-1/2 top-1/2 translate-x-[-50%] translate-y-[-50%] text-7xl text-blue-100">0</p>
  </div>
  <section v-if="isOpen" class="h-screen w-screen bg-blue-100">
    <div class="relative left-1/4 top-1/4">
      <h2>Welcome!</h2>
      <p>Filler text...</p>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-screen bg-blue-200">
    <div class="relative left-1/4 top-1/4" data-aos="fade-up">
      <h2>Cult of Domesticity</h2>
      <p>Filler text...</p>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-screen bg-blue-300">
    <div class="relative left-1/4 top-1/4" data-aos="fade-up">
      <h2>Self-Consciousness!</h2>
      <p>Filler text...</p>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-screen bg-blue-400">
    <div class="relative left-1/4 top-1/4" data-aos="fade-up">
      <h2>Solitude</h2>
      <p>Filler text...</p>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-screen bg-blue-500">
    <div class="relative left-1/4 top-1/4" data-aos="fade-up">
      <h2>Sexuality</h2>
      <p>Filler text...</p>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-screen bg-blue-600">
    <div class="relative left-1/4 top-1/4" data-aos="fade-up">
      <h2>Escape</h2>
      <p>Filler text...</p>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-screen bg-blue-700">
    <div class="relative left-1/4 top-1/4" data-aos="fade-up">
      <h2>Freedom</h2>
      <p>Filler text...</p>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-screen bg-blue-800">
    <div class="relative left-1/4 top-1/4" data-aos="fade-up">
      <h2>Modern Wokeness</h2>
      <p>Filler text...</p>
    </div>
  </section>
</template>
