<template>
  <main class="carousel horizontal snap">
    <header class="centred slide">
      <img class="title" src="img/title.png" alt="The Making Known" />
    </header>

    <div class="centred slide">
      <div class="text">
        <p>
          This is a narrated encounter with posters designed by the Nazi German government to
          communicate with the occupied nations of Belgium, France, and Luxembourg during the
          Second World War. The posters are part of the Tetlie Collection of WWII Propaganda
          Posters at the Flaten Art Museum at St Olaf College in Northfield, Minnesota.
        </p>

        <p>
          The encounter takes form through three audio letters written by the artist to individuals of
          relevance to the preservation and interpretation of the posters and their twenty-first century
          meaning: a curator, a paper conservator, and a poet. Each letter lasts between fifteen and
          twenty minutes.
        </p>

        <p>
          Please put on your headphones, turn off the ringer of your device, and when you are
          ready, proceed to the menu to select one of the audio letters of <em>The Making Known</em>.
        </p>

        <p class="centred">
          <button class="arrow right inline" title="forward"></button>
        </p>
      </div>
    </div>

    <div class="centred slide">
<!--      <Menu @select="handleSelect" />-->
    </div>

    <div class="centred slide">
<!--      <Player piece={currentPiece} bind:this={player} on:ended={clearHash} />-->
    </div>

    <div class="centred slide">
      <div class="text">
        <p>
          <em>The Making Known</em> was written and created by <a href="https://nemer.be" target="_blank">Benny Nemer</a>
          to accompany a scenography of flowers, paper mobiles, and a selection of posters from the Tetlie
          Collection, exhibited in a solo exhibition at the Flaten Art Museum at St Olaf College in the
          winter of 2022. The project was commissioned by museum Director and Curator Jane
          Becker Nelson with financial support from Institute of Museum and Library Services.
          Website programming by Nikita Gaidakov.
        </p>
      </div>
    </div>

    <div class="background default" :class="{ show: !viewingPlayer }"></div>
    <div class="background jane" :class="{ class: viewingPlayer && piece === Piece.Jane }"></div>
    <div class="background dianna" :class="{ class: viewingPlayer && piece === Piece.Dianna }"></div>
    <div class="background paul" :class="{ class: viewingPlayer && piece === Piece.Paul }"></div>
  </main>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue'

import { Piece } from '@/types'

const introScrollWaitTime = 2000
const autoScrollSpeedSlow = 1400

const props = withDefaults(defineProps<{
  piece: Piece
}>(), {
  piece: Piece.Jane
})

const loaded = ref(false)
const itsTimeToScrollToIntro = ref(false)
const userHasScrolled = ref(false)
const autoscrolling = ref(false)
const snappedToSlide = ref(true)

const viewingPlayer = computed(() => false)
</script>

<style scoped>
.carousel {
  height: 100%;
  width: 100%;
  overflow: auto;
  display: flex;
}

.carousel.horizontal {
  scroll-snap-type: x mandatory;
  flex-direction: row;
}

.centred {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.slide {
  flex: none;
  height: 100%;
  width: 100%;
}

.carousel.snap > .slide {
  scroll-snap-stop: always;
  scroll-snap-align: center;
}

.title {
  max-height: 70%;
  max-width: 90%;
}

.background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  background-size: cover;

  opacity: 0;
  transition: opacity 300ms ease-out;
  will-change: opacity;
}

.background.show {
  opacity: 1;
}

.background.default {
  background-image: url(/img/bg-main.jpeg);
  background-position: 95% 75%;
}

.background.jane {
  background-image: url(/img/bg-jane.jpeg);
  background-position: 32% 0;
}

.background.dianna {
  background-image: url(/img/bg-dianna.jpeg);
  background-position: 80% 80%;
}

.background.paul {
  background-image: url(/img/bg-paul.jpeg);
  background-position: 0 0;
}

button.arrow {
  width: 5em;
}

button.arrow.left {
  background-image: url(/img/back.png);
}

button.arrow.right {
  background-image: url(/img/forward.png);
}

button.inline {
  margin-top: 0.6em;
}

.arrow.side {
  position: absolute;
  bottom: 12%;
  --margin: calc(22% - 6em);
}

@media (max-width: 1000px) {
  .arrow.side {
    display: none;
  }
}

@media (hover: none) {
  .arrow.side {
    display: none;
  }
}

@media (hover: hover) and (min-width: 1000px) {
  .arrow.inline {
    display: none;
  }
}

.arrow.side.left {
  left: var(--margin);
}

.arrow.side.right {
  right: var(--margin);
}
</style>
