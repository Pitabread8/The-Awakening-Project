<script setup>
useHead({
  script: [{ src: "https://unpkg.com/aos@next/dist/aos.js", body: true }],
});
</script>

<script>
import prelude from "../assets/audio/prelude.mp3";
import milliondollarman from "../assets/audio/milliondollarman.mp3";
import poetpeasant from "../assets/audio/poetpeasant.mp3";
import blackbird from "../assets/audio/blackbird.mp3";
import fadeintoyou from "../assets/audio/fadeintoyou.mp3";
import lookbridge from "../assets/audio/lookbridge.mp3";
import zampa from "../assets/audio/zampa.mp3";
import seabirds from "../assets/audio/seabirds.mp3";

export default {
  beforeMount() {
    window.addEventListener("scroll", this.handleScroll);
  },
  mounted() {
    this.audio = new Audio(prelude);
  },
  beforeUnmount() {
    window.removeEventListener("scroll", this.handleScroll);
    this.audio.pause();
  },
  data() {
    return {
      isOpen: false,
      isShown: false,
      a: 0,
      audio: null,
      button: {
        arrow: "mdi:chevron-right",
      },
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

      // let audios = [prelude, milliondollarman, zampa, blackbird, fadeintoyou, lookbridge, poetpeasant, seabirds];
      let audios = [prelude, milliondollarman, zampa, blackbird, fadeintoyou, lookbridge, seabirds];

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
    openModal() {
      this.isShown = !this.isShown;
      this.button.arrow = this.isShown ? "mdi:chevron-down" : "mdi:chevron-right";
    },
  },
};
</script>

<template>
  <Head>
    <Link rel="stylesheet" href="https://unpkg.com/aos@next/dist/aos.css" />
  </Head>
  <section v-if="!isOpen" class="h-screen w-screen bg-blue-800">
    <button id="open" @click="openPage()" class="fixed left-1/2 top-1/2 h-36 w-36 translate-x-[-50%] translate-y-[-50%] rounded-full bg-blue-50">
      <Icon class="absolute left-1/2 top-1/2 translate-x-[-50%] translate-y-[-50%] text-8xl text-blue-800" name="mdi:play" />
    </button>
  </section>
  <section v-if="isOpen" class="h-screen w-auto bg-blue-700">
    <div class="relative p-40 text-blue-50">
      <h2>Welcome!</h2>
      <p>
        <em>The Awakening</em>
        by Kate Chopin deals with a character&#39;s realization of her true self, through an <span class="font-serif">awakening</span>. This concept stood out to me, as it will always be relatable and relevant to anyone, anywhere, at any time. I set out to investigate the idea of an awakening in the
        consciousness and what it means to the real world. My project identifies seven central themes in the book and connects them to analyses of their broader meaning.
        <br />
        <br />
        <em>The Awakening</em>
        initially seems like just a feminist period piece, but upon closer inspection, it has a deeper meaning about consciousness and self that anyone can learn from. The theme of our Comparative Literature course is the concept of <span class="font-serif">Human</span>. <em>The Awakening</em>
        grapples with these questions, showing the human transformation in the protagonist from one tied down by society to one who is free and completely herself. Through dealing with the concept of self, the book addresses humanity and how to define it.
        <br />
        <br />
        Often when we think about humanity, what makes us human, and who is inhuman, we tend to think about social constructs—race, gender, nationality, sexuality—and the conflicts associated with them. But Kate Chopin looks at it differently; one&#39;s humanity isn&#39;t defined by others, but
        simply through one&#39;s own journey in self-consciousness.
      </p>
    </div>
  </section>
  <section v-if="isOpen" class="h-auto w-auto bg-blue-600">
    <div class="relative flex flex-row gap-8 p-40">
      <img class="h-auto w-full" src="~/assets/images/wedding.jpeg" data-aos="fade-up" data-aos-duration="3000" />
      <div>
        <h2>Cult of True Womanhood</h2>
        <p>
          The Cult of True Womanhood is an ideology and system that dominated middle and upper classes in 19th century United States.
          <a class="text-blue-50 hover:underline" href="https://digital.lib.washington.edu/researchworks/bitstream/handle/1773/33518/Mizic_washington_0250O_14462.pdf">Its main tenets are piety (mother), purity (daughter), submissiveness (sister), and domesticity (wife).</a>
          These ideas could be found everywhere in culture, from societal norms to popular media. Piety represents religious dedication, Purity means physical virginity or innocence, Submission is to always listen to a man, and Domesticity was about staying at and tending to the home at all times.
          All four of these are expected of Edna Pontellier, and she feels weighed down by them&#8212;trapped like a bird. Kate Chopin invokes the metaphor of a caged parrot, something that Edna strongly identifies with. In the course of
          <em>The Awakening</em>
          , Edna tries to overcome these virtues: her marriage was a rebellion against her family's religion, she engages in both emotional and sexual extramarital affairs, she stops readily listening to her husband. Yet, at the very end of the book, she notes that she's not fully able to escape
          Domesticity; her children are "<span class="font-serif">like antagonists who had overcome her; who had overpowered and sought to drag her into the soul&#39;s slavery for the rest of her days</span>" (Chopin 163). Mademoiselle Reisz ties the Cult of True Womanhood and bird imagery together
          beautifully, saying "&#39;<span class="font-serif">The bird that would soar above the level plain of tradition and prejudice must have strong wings. It is a sad spectacle to see the weaklings bruised, exhausted, fluttering back to earth</span>&#39;" (129).
        </p>
      </div>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-auto bg-blue-500">
    <div class="relative flex flex-row gap-8 p-40">
      <img class="h-96 w-auto" src="~/assets/images/gulf.jpg" data-aos="fade-up" data-aos-duration="3000" />
      <div>
        <h2>Self-Consciousness</h2>
        <p>
          Edna's self-consciousness in
          <em>The Awakening</em>
          is represented in a multitude of ways. Art has a huge impact on her; she dedicates much of her time to painting and listens to music passionately. Nature is also important: Edna often expresses enjoyment when she's at the beach, as she looks out in the Gulf. Edna's sisterhood with other
          women, particularly Adele Ratignolle and Mademoiselle Reisz, plays an important role. It's with these women that she is able to confess her feelings and is also supported and encouraged to be her true self&#8212;the book clearly passes the Bechdel test.
          <br />
          <br />
          It's argued that these aspects of self-consciousness are more important than the more obvious themes of desire and feminism.
          <a class="text-blue-50 hover:underline" href="https://scholarcommons.sc.edu/cgi/viewcontent.cgi?article=1092&context=tor"
            >The book isn't just about Edna's role as a woman&#8212;she doesn't even leave the patriarchal social construct of
            <em>The Awakening</em>
            &#8212;but about a transformation and rediscovery of consciousness that can apply to anyone.</a
          >
          Chopin is inviting readers to an individual's journey of realizing their true self in a society they don't quite fit in.
        </p>
      </div>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-auto bg-blue-400">
    <div class="h-min p-40">
      <div class="relative flex flex-row gap-8">
        <img class="h-96 w-auto" src="~/assets/images/rainy.jpeg" data-aos="fade-up" data-aos-duration="3000" />
        <div>
          <h2 class="text-center">Solitude</h2>
          <p>
            Solitude is a clear theme in <em>The Awakening</em>. In many of the scenes in the book, only Edna is present, and Chopin's original title for the book was "<span class="font-serif">A Solitary Soul</span>". The symbolism of the sea and birds are often associated with loneliness, just as
            they are in the book.
          </p>
        </div>
        <img class="h-96 w-auto" src="~/assets/images/beach.jpeg" data-aos="fade-up" data-aos-duration="3000" />
      </div>
      <svg class="relative bottom-0 z-50 h-1/4 w-full" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 24 150 28" preserveAspectRatio="none" shape-rendering="auto">
        <defs>
          <path id="gentle-wave" d="M-160 44c30 0 58-18 88-18s 58 18 88 18 58-18 88-18 58 18 88 18 v44h-352z" />
        </defs>
        <g class="parallax">
          <use xlink:href="#gentle-wave" x="48" y="0" fill="rgba(155,155,155,0.7" />
          <use xlink:href="#gentle-wave" x="48" y="3" fill="rgba(255,255,255,0.5)" />
          <use xlink:href="#gentle-wave" x="48" y="5" fill="rgba(185,185,185,0.3)" />
          <use xlink:href="#gentle-wave" x="48" y="7" fill="#eee" />
        </g>
      </svg>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-auto bg-blue-300">
    <div>
      <div class="relative flex flex-row gap-8 px-40 pb-4 pt-40">
        <img class="h-full w-auto" src="~/assets/images/pronouneye.jpeg" data-aos="fade-up" data-aos-duration="3000" />
        <div>
          <h2>Sexuality</h2>
          <p>
            Edna's discovery of her sexuality and desire is a powerful way to begin her transformation. When Edna starts listening to her own feelings and engaging in relationships that truly meet her needs, she has a better understanding of herself as a human. This also ties into feminism: once a
            woman understands and prioritizes her desire and sensuality, she can begin the process of overcoming society's hurdles. Likewise, not allowing one to explore or be true to one's sexuality is oppression as it limits their ability to really be human. This concept is also explored in Leslie
            Feinberg's <em>Stone Butch Blues</em>, in which the main character has to undergo physical and sexual abuse because she's unable to deny her sexuality or conform to society's expectations.
            <a class="text-blue-50 hover:underline" href="https://www.nytimes.com/2020/02/05/books/review/kate-chopin-the-awakening.html">Pleasure and sensation isn't gratuitous or salacious for people who've been oppressed and gaslit by society, it's an essential reorientation.</a>
            <br />
            <br />
          </p>
        </div>
      </div>
      <p class="w-full px-40">
        Edna experiences sensuality with nature, namely the sea. "<span class="font-serif"
          >The voice of the sea is seductive; never ceasing, whispering, clamoring, murmuring, inviting the soul to wander for a spell in abysses of solitude; to lose itself in mazes of inward contemplation. The voice of the sea speaks to the soul. The touch of the sea is sensuous, enfolding the
          body in its soft, close embrace</span
        >" (Chopin 25). The sea's personification mirrors the emotions Edna experiences as she explores her sexuality. It's another catalyst for Edna's awakening, and it plays an important role in her liberation later on.
      </p>
    </div>
  </section>
  <section v-if="isOpen" class="h-screen w-auto bg-blue-200">
    <div class="relative flex flex-row gap-8 py-40 px-80">
      <img class="h-auto w-1/3" src="~/assets/images/drowning.jpeg" data-aos="fade-up" data-aos-duration="3000" />
      <!-- <div class="w-1/2"></div> -->
      <div>
        <h2>Escape</h2>
        <p>
          Suicide has always been a heavy topic in literature. While other difficult things, like killing another person, seem black and white, the idea of killing oneself is always complex. Yet its use in <em>The Awakening</em> is powerful and symbolic. Firstly, Chopin completes the book suggesting
          Edna drowns herself. The inevitable unknown of an ending, compounded by it being open to interpretation, makes Edna's death seem more peaceful than it normally is. Secondly, the suicide can be seen as a beautiful act, considering the motivation and circumstances. Edna has been feeling
          intensely trapped and she's realized that she'll never be free. Compared to living in a metaphorical cage and death, death is liberty, an escape.
          <a class="text-blue-50 hover:underline" href="https://digital.lib.washington.edu/researchworks/bitstream/handle/1773/33518/Mizic_washington_0250O_14462.pdf"
            >There's also significance of birds and sea in this scene. The sea is literally represented as she drowns, while bird imagery often represents souls in the mythological escape to the afterlife.</a
          >
        </p>
      </div>
    </div>
  </section>
  <!-- <section v-if="isOpen" class="h-screen w-auto bg-blue-200">
    <div class="relative p-40" data-aos="fade-up" data-aos-delay="1000" data-aos-duration="3000">
      <h2>Freedom</h2>
      <p>Filler text...</p>
    </div>
  </section> -->
  <section v-if="isOpen" class="h-full w-auto overflow-hidden bg-blue-100">
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
    <div class="relative p-40" data-aos="fade-up" data-aos-delay="1000" data-aos-duration="3000">
      <h2>Modern Wokeness</h2>
      <p>
        In the book, the awakening represents Edna unlocking a part of her self, her personality. This concept of being awake has been used in similar contexts for a long time in other places. During the 1860 American presidential election, a political organization called the Wide Awakes consisting
        of and working with young men campaigned for Abraham Lincoln. In the early 1900s, the term <span class="font-serif">woke</span> was used in songs to warn Black people of the dangers in the South. By the mid-1900s, being <span class="font-serif">woke</span> meant you were culturally and
        politically aware. It was used largely in AAVE, but hadn't become very mainstream. Then, in the 2000s, it started to become popular online. As the Black Lives Matter (BLM) movement gained prominence, it was adopted by non-Black Americans to signal support. However, in the last few years, the
        term has been used disparagingly by conservatives to mock what they believe is performative activism.
      </p>
      <button @click="openModal()" class="flex flex-row items-center justify-center text-blue-950">
        <Icon class="text-4xl" :name="button.arrow" />
        <p>Poet Juliana Gray adapted the story of <em>The Awakening</em> into a satirical poem that reflects the similitude between the book and being <span class="font-serif">woke.</span></p>
      </button>
      <div v-if="isShown">
        <p class="font-serif">
          A green and yellow parrot, which hung in a cage outside the door, kept repeating over and over: "<em>Je ne peux pas respirer</em>! I can&#39;t breathe!"
          <br />
          <br />
          Mr. Pontellier, unable to watch Fox News with any degree of comfort, arose with an exclamation of disgust. What an annoyance the bird was. Did it not know that all lives mattered?
          <br />
          <br />
          "Eric Garner! Trayvon Martin! Sandra Bland! Say their names!" the bird shouted.
          <br />
          <br />
          Mr. Pontellier looked out toward the beach. His two sturdy sons and their nurse were approaching, followed by his wife and young Robert Lebrun.
          <br />
          <br />
          "You are burnt beyond recognition," he said, looking at his wife as one looks at a valuable piece of property which has suffered some damage. "You are quite as dark as the quadroon nurse."
          <br />
          <br />
          "Mr. Pontellier," the nurse said stiffly, "I have asked you repeatedly not to use that word or any other hate speech. My name is Denise, and I demand respect. And please tell your children not to touch my hair."
          <br />
          <br />
          <span class="inline-block w-full text-center">&#x2022; &#x2022; &#x2022;</span>
          <br />
          <br />
          Robert Lebrun plucked an orange from the low-hanging branch of a tree and offered it to her. "I am very surprised you have not seen the video already," he told her. "It has been all over social media."
          <br />
          <br />
          "Oh," she said, "I am not very political."
          <br />
          <br />
          "But how can you not be political when we live in the midst of systemic social injustice? We must hold the police accountable! We must bear witness! Here, sit by me; Madame Antoine left us a meal of locally sourced, farm-to-table foods before she joined the LGBTQIA pride parade. How lucky
          we are not to live in a food desert! — which of course are most often found in low-income urban communities inhabited by people of color. Here, we can watch the video on my phone while we eat. Trigger warning, darling."
          <br />
          <br />
          Edna reluctantly seated herself beside him on the chaise while Robert opened the YouTube app. Soon the sounds of shouts and gunfire could be heard.
          <br />
          <br />
          "You see?" Robert asked, leaning close and breathing softly into her ear. "This is just one example of the racially motivated violence endemic to our patriarchal society and the gun culture. And how do you like the kale? I massaged it myself."
          <br />
          <br />
          <span class="inline-block w-full text-center">&#x2022; &#x2022; &#x2022;</span>
          <br />
          <br />
          Mrs. Pontellier and Madame Ratignolle seated themselves in the shade of the porch and fanned themselves. Madame Ratignolle produced a diminutive roll of needlework, some little garment she was making for one of her children. Edna rested her eyes upon the sea.
          <br />
          <br />
          "Of what are you thinking, my dear?" asked Madame Ratignolle of her companion, whose countenance she had been watching with amused attention.
          <br />
          <br />
          "I was thinking about white privilege and intersectionality," said Edna, "and how it seems to me that these things do, in fact, shape our perceptions and our lives in ways of which we are blissfully unaware. I was thinking of systemic gendered double standards, how Léonce went to dinner
          and billiards at Klein&#39;s as if it were the most natural thing in the world, yet I am scolded like a child if I choose to go walking than sit at home to receive social calls. I was thinking of the shocking income inequality in this country, and how the middle class is being squeezed out
          of existence while the one percent continue to amass great wealth. I was thinking that perhaps my servants do not entirely enjoy being my servants."
          <br />
          <br />
          Mrs. Ratignolle frowned. "My dear, I do not think this hot sun is good for you. Perhaps you should consider having another baby."
          <br />
          <br />
          <span class="inline-block w-full text-center">&#x2022; &#x2022; &#x2022;</span>
          <br />
          <br />
          When Mr. Pontellier came home at last, he discovered his wife lying in the hammock. "Edna! What folly is this? You will take cold; come in."
          <br />
          <br />
          "I am not cold; I have my shawl."
          <br />
          <br />
          "The mosquitoes will devour you. I can&#39;t permit you to stay out there all night."
          <br />
          <br />
          "There are no mosquitoes, and that is a microagression. Please respect my autonomous personhood. This is a safe space."
          <br />
          <br />
          Léonce lit a cigar. His wife was clearly ill or insane, perhaps both. He would contact his friend in the city, Doctor Mandelet. Together the two wealthy white men would decide how best to legislate his wife&#39;s body.
          <br />
          <br />
          <span class="inline-block w-full text-center">&#x2022; &#x2022; &#x2022;</span>
          <br />
          <br />
          Edna found Madame Ratignolle in the salon, her face drawn and pinched, her blue eyes haggard. "Where is the doctor?" she cried.
          <br />
          <br />
          "Do you mean that you do not have a doula?" Edna asked. "Did you not read the articles I sent you about low-intervention birth plans, African birthing swings, or dolphin-assisted births? Did you read the articles about the dangers of vaccination and the benefits of co-sleeping? My dear
          Adèle, do you even have a birth plan?"
          <br />
          <br />
          "I am in a great deal of pain," Madame Ratignolle gasped.
          <br />
          <br />
          "Ah, it is just as I feared!" Edna cried. "I said as much to Alcée Arobin in bed last night, just after we brought each other to consensual mutual orgasm."
          <br />
          <br />
          Madame Ratignolle swooned, and the baby plopped onto the floor from beneath her skirts. Edna bent gracefully and gathered the placenta. She would leave a restorative placenta smoothie recipe with the cook, a woman who earned shockingly little compared to a man doing equal work.
          <br />
          <br />
          <span class="inline-block w-full text-center">&#x2022; &#x2022; &#x2022;</span>
          <br />
          <br />
          The waters of the Gulf stretched out before her. Edna sighed; it was no use. Robert had proven himself to be a manspreader, a mansplainer, a product of rape culture. Arobin&#39;s dreadlocks were an unforgivable appropriation of black culture, and Léonce&#39;s new profile pic showed him
          sporting a BLUE LIVES MATTER pin at a Trump rally. Adèle chattered only about her baby and the return of pumpkin spice latte season. There was no possibility, Edna thought, of her continuing in this life now that she was truly woke.
          <br />
          <br />
          She cast off her garments, oppressive and hyper-sexualized items produced by abused and exploited workers, and for the first time in her life stood naked and un-body-shamed in the open air.
          <br />
          <br />
          She walked into the sea. "Be the change you wish to see in the world," she sighed as she swam out, farther and farther, until exhaustion overpowered her.
          <br />
          <br />
          Two strong women of color watched from the shore.
          <br />
          <br />
          "Wow, talk about white privilege," Denise said.
          <br />
          <br />
          "I heard that," replied her trans Latina friend Mariequita. "And you know Ghandi never actually said that."
          <br />
          <br />
          Denise shook her head. "She probably learned it from a fucking bumper sticker."
        </p>
      </div>
    </div>
    <div v-if="isOpen" class="fixed right-[3%] top-1/2 h-36 w-36 translate-y-[-50%] rounded-full bg-blue-50 opacity-80">
      <p id="number" class="absolute left-1/2 top-1/2 translate-x-[-50%] translate-y-[-50%] text-7xl text-blue-950">0</p>
    </div>
  </section>
</template>
