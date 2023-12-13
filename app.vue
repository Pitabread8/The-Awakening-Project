<!-- 
font change for quotes
update songs
-->

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
  <div v-if="isOpen" class="fixed right-[3%] top-1/2 h-36 w-36 translate-y-[-50%] rounded-full bg-blue-950">
    <p id="number" class="absolute left-1/2 top-1/2 translate-x-[-50%] translate-y-[-50%] text-7xl text-blue-100">0</p>
  </div>
  <section v-if="isOpen" class="h-screen w-auto bg-blue-100">
    <div class="relative px-40 pt-40">
      <h2>Welcome!</h2>
      <p>
        <em>The Awakening</em> by Kate Chopin deals with a character&#39;s realization of her true self, through an "awakening." This concept stood out to me, as it will always be relatable and
        relevant to anyone, anywhere, at any time. I set out to investigate the idea of an awakening in the consciousness and what it means to the real world. My project identifies seven central
        themes in the book and connects them to analyses of their broader meaning. <br />
        <br />
        <em>The Awakening</em> initially seems like just a feminist period piece, but upon closer inspection, it has a deeper meaning about consciousness and self that anyone can learn from. The theme
        of our Comparative Literature course is the concept of "Human." <em>The Awakening</em> grapples with these questions, showing the human transformation in the protagonist from one tied down by
        society to one who is free and completely herself. Through dealing with the concept of self, the book addresses humanity and how to define it. <br />
        <br />
        Often when we think about humanity, what makes us human, and who is inhuman, we tend to think about social constructs—race, gender, nationality, sexuality—and the conflicts associated with
        them. But Kate Chopin looks at it differently; one&#39;s humanity isn&#39;t defined by others, but simply through one&#39;s own journey in self-consciousness.
      </p>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-auto bg-blue-200">
    <div class="relative px-40 pt-40" data-aos="fade-up">
      <h2>Cult of True Womanhood</h2>
      <p>
        The Cult of True Womanhood is an ideology and system that dominated middle and upper classes in 19th century United States.
        <a class="text-blue-50 hover:underline" href="https://digital.lib.washington.edu/researchworks/bitstream/handle/1773/33518/Mizic_washington_0250O_14462.pdf">
          Its main tenets are piety (mother), purity (daughter), submissiveness (sister), and domesticity (wife).
        </a>
        These ideas could be found everywhere in culture, from societal norms to popular media. Piety represents religious dedication, Purity means physical virginity or innocence, Submission is to
        always listen to a man, and Domesticity was about staying at and tending to the home at all times. All four of these are expected of Edna Pontellier, and she feels weighed down by
        them--trapped like a bird. Kate Chopin invokes the metaphor of a caged parrot, something that Edna strongly identifies with. In the course of <em>The Awakening</em>, Edna tries to overcome
        these virtues: her marriage was a rebellion against her family's religion, she engages in both emotional and sexual extramarital affairs, she stops readily listening to her husband. Yet, at
        the very end of the book, she notes that she's not fully able to escape Domesticity; her children are "like antagonists who had overcome her; who had overpowered and sought to drag her into
        the soul&#39;s slavery for the rest of her days" (Chopin 163). Mademoiselle Reisz ties the Cult of True Womanhood and bird imagery together beautifully, saying "&#39;The bird that would soar
        above the level plain of tradition and prejudice must have strong wings. It is a sad spectacle to see the weaklings bruised, exhausted, fluttering back to earth&#39;" (129).
      </p>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-auto bg-blue-300">
    <div class="relative px-40 pt-40" data-aos="fade-up">
      <h2>Self-Consciousness</h2>
      <p>
        Edna's self-consciousness in <em>The Awakening</em> is represented in a multitude of ways. Art has a huge impact on her; she dedicates much of her time to painting and listens to music
        passionately. Nature is also important: Edna often expresses enjoyment when she's at the beach, as she looks out in the Gulf. Edna's sisterhood with other women, particularly Adele Ratignolle
        and Mademoiselle Reisz, plays an important role. It's with these women that she is able to confess her feelings and is also supported and encouraged to be her true self--the book clearly
        passes the Bechdel test. <br />
        <br />
        It's argued that these aspects of self-consciousness are more important than the more obvious themes of desire and feminism.
        <a class="text-blue-50 hover:underline" href="https://scholarcommons.sc.edu/cgi/viewcontent.cgi?article=1092&context=tor">
          The book isn't just about Edna's role as a woman--she doesn't even leave the patriarchal social construct of <em>The Awakening</em>--but about a transformation and rediscovery of
          consciousness that can apply to anyone.
        </a>
        Chopin is inviting readers to an individual's journey of realizing their true self in a society they don't quite fit in.
      </p>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-auto bg-blue-400">
    <div class="relative px-40 pt-40" data-aos="fade-up">
      <h2>Solitude</h2>
      <p>
        Solitude is a clear theme in <em>The Awakening</em>. In many of the scenes in the book, only Edna is present, and Chopin's original title for the book was "A Solitary Soul". The symbollism of
        the sea and birds are often associated with loneliness, just as they are in the book.
      </p>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-auto bg-blue-500">
    <div class="relative px-40 pt-40" data-aos="fade-up">
      <h2>Sexuality</h2>
      <p>Filler text...</p>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-auto bg-blue-600">
    <div class="relative px-40 pt-40" data-aos="fade-up">
      <h2>Escape</h2>
      <p>Filler text...</p>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-auto bg-blue-700">
    <div class="relative px-40 pt-40" data-aos="fade-up">
      <h2>Freedom</h2>
      <p>Filler text...</p>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-auto overflow-hidden bg-blue-800">
    <div class="relative top-28 px-40">
      <div class="bird-container bird-container--one">
        <div class="bird bird--one"></div>
      </div>
      <div class="bird-container bird-container--two">
        <div class="bird bird--two"></div>
      </div>
      <div class="bird-container bird-container--three">
        <div class="bird bird--three"></div>
      </div>
      <div class="bird-container bird-container--four">
        <div class="bird bird--four"></div>
      </div>
    </div>
    <div class="relative px-40 pt-40" data-aos="fade-up">
      <h2>Modern Wokeness</h2>
      <p>Filler text...</p>
    </div>
    <div v-if="!isOpen" class="fixed left-0 top-0 h-screen w-auto bg-blue-100">
      <button id="open" @click="openPage()" class="fixed left-1/2 top-1/2 h-36 w-36 translate-x-[-50%] translate-y-[-50%] rounded-full bg-blue-950 text-8xl">
        <Icon class="absolute left-1/2 top-1/2 translate-x-[-50%] translate-y-[-50%] text-blue-100" name="mdi:play" />
      </button>
    </div>
  </section>
</template>
