<template>
  <div class="outfit-builder">
    <!-- Left column: thumbnails -->
    <div class="thumbnails">
      <!-- Jacket section -->
      <div class="section">
        <h3>Select a Jacket</h3>
        <div class="thumbs">
          <div
            v-for="jacket in jackets"
            :key="jacket.name"
            class="thumb-container"
            @click="selections.jacket = jacket"
            :class="{ selected: selections.jacket.name === jacket.name }"
          >
            <img
              :src="`${basePath}images/jacketSwatches/${jacket.swatch}`"
              :alt="jacket.name"
            />
            <p class="thumb-label">{{ jacket.name }}</p>
          </div>
        </div>
      </div>

      <!-- Kilt section -->
      <div class="section">
        <h3>Select a Kilt</h3>
        <div class="thumbs">
          <div
            v-for="kilt in kilts"
            :key="kilt.name"
            class="thumb-container"
            @click="selections.kilt = kilt"
            :class="{ selected: selections.kilt.name === kilt.name }"
          >
            <img
              :src="`${basePath}images/${kilt.swatch}`"
              :alt="kilt.name"
            />
            <p class="thumb-label">{{ kilt.name }}</p>
          </div>
        </div>
      </div>
    
      <!-- Tie section -->
      <div class="section">
        <h3>Select a Tie</h3>
        <div class="thumbs">
          <div
            v-for="tie in ties"
            :key="tie.name"
            class="thumb-container"
            @click="selections.tie = tie"
            :class="{ selected: selections.tie.name === tie.name }"
          >
            <img
              :src="`${basePath}images/${tie.swatch}`"
              :alt="tie.name"
            />
            <p class="thumb-label">{{ tie.name }}</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Right column: preview -->
    <div class="preview">
  <div class="preview-stack">
    <img :src="`${basePath}images/baseBody.png`" class="base-body" />
    <img :src="`${basePath}images/jacketColors/${selections.jacket.preview}`" class="jacket" />
    <img :src="`${basePath}images/tieColors/${selections.tie.preview}`" class="tie" />
    <img :src="`${basePath}images/${selections.kilt.preview}`" class="kilt" />
  </div>
  </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      jackets: [
        { name: 'Charcoal',       swatch: 'swatch-charcoal.png',      preview: 'jacket-charcoal.png' },
        { name: 'Midnight Blue',  swatch: 'swatch-midnightBlue.png',  preview: 'jacket-midnightBlue.png' },
        { name: 'Light Grey',     swatch: 'swatch-lightGrey.png',     preview: 'jacket-lightGrey.png' },
        { name: 'Lovat Blue',     swatch: 'swatch-lovatBlue.png',     preview: 'jacket-lovatBlue.png' },
        { name: 'Moss Green',     swatch: 'swatch-mossGreen.png',     preview: 'jacket-mossGreen.png' },
        { name: 'Peat Brown',     swatch: 'swatch-peatBrown.png',     preview: 'jacket-peatBrown.png' }
      ],
      kilts: [
        { name: 'Ancient Patriot',    swatch: 'swatch-ancientPatriot.png',    preview: 'kilt-ancientPatriot.png' },
        { name: 'Beatson',            swatch: 'swatch-beatson.png',           preview: 'kilt-beatson.png' },
        { name: 'Buchanan Hunting',   swatch: 'swatch-buchanan.png',          preview: 'kilt-buchanan.png' },
        { name: 'Grey Slanj',         swatch: 'swatch-greySlanj.png',         preview: 'kilt-greySlanj.png' },
        { name: 'Isle of Skye',       swatch: 'swatch-isleOfSkye.png',        preview: 'kilt-isleOfSkye.png' },
        { name: 'Manx Hunting',       swatch: 'swatch-manx.png',              preview: 'kilt-manx.png' },
        { name: 'Maple Leaf',         swatch: 'swatch-mapleLeaf.png',         preview: 'kilt-mapleLeaf.png' },
        { name: 'Spirit of Glasgow',  swatch: 'swatch-spiritOfGlasgow.png',   preview: 'kilt-spiritOfGlasgow.png' },
        { name: 'St Mirren FC',       swatch: 'swatch-stMirren.png',          preview: 'kilt-stMirren.png' },
        { name: 'Weathered Patriot',  swatch: 'swatch-weatheredPatriot.png',  preview: 'kilt-weatheredPatriot.png' },
      ],
      ties: [
        { name: 'Black',          swatch: '/tieSwatches/swatch-black.png',      preview: 'tie-black.png' },
        { name: 'Champagne',      swatch: '/tieSwatches/swatch-champagne.png',  preview: 'tie-champagne.png' },
        { name: 'Claret',         swatch: '/tieSwatches/swatch-claret.png',     preview: 'tie-claret.png' },
        { name: 'Bottle Green',   swatch: '/tieSwatches/swatch-green.png',      preview: 'tie-green.png' },
        { name: 'Dark Grey',      swatch: '/tieSwatches/swatch-grey.png',       preview: 'tie-grey.png' },
        { name: 'Navy',           swatch: '/tieSwatches/swatch-navy.png',       preview: 'tie-navy.png' },
        { name: 'Baby Pink',      swatch: '/tieSwatches/swatch-pink.png',       preview: 'tie-pink.png' },
        { name: 'Purple',         swatch: '/tieSwatches/swatch-purple.png',     preview: 'tie-purple.png' },
        { name: 'Dark Red',       swatch: '/tieSwatches/swatch-red.png',        preview: 'tie-red.png' },
        { name: 'Silver',         swatch: '/tieSwatches/swatch-silver.png',     preview: 'tie-silver.png' },
      ],
      selections: {
        jacket: { name: 'Charcoal', swatch: 'swatch-charcoal.png', preview: 'jacket-charcoal.png' },
        kilt: { name: 'Isle of Skye', swatch: 'swatch-isleOfSkye.png', preview: 'kilt-spiritOfGlasgow.png' },
        tie: { name: 'Black', swatch: 'swatch-black.png', preview: 'tie-black.png' }
      }
    }
  },

computed: {
  basePath() {
    return import.meta.env.BASE_URL || '/'
  }
}
}
</script>

<style>
#app {
  width: 100%;
}

body {
  background-color: white;
  color: #000;
}

.outfit-builder {
  display: grid;
  grid-template-columns: 75% 25%;
  width: 100%;
}

/* Thumbnail sections */
.thumbnails {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.section {
  padding: 10px;
  background: #f9f9f9;
  border-radius: 6px;
  border: 1px solid #ddd;
}

.thumbs {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  justify-content: flex-start;
}

.thumb-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  cursor: pointer;
}

.thumb-container img,
.thumbs img {
  width: 100px;
  height: 100px;
  object-fit: cover;
  border: 2px solid transparent;
  border-radius: 4px;
  cursor: pointer;
}

.thumb-container.selected img,
.thumbs img.selected {
  border-color: #000;
}

.thumb-label {
  margin-top: 5px;
  font-size: 14px;
  color: #333;
}

/* Preview area */
.preview {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

.preview-stack {
  position: relative;
  width: 100%;
  max-width: 600px;
  aspect-ratio: 3 / 4;
}

/* Base body scales fluidly */
.base-body {
  width: 100%;
  height: auto;
  display: block;
  position: relative;
  z-index: 0;
}

/* Overlays (top half) */
.jacket,
.tie {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 100%;   /* scale with baseBody */
  height: auto;
}

.jacket { z-index: 2; }
.tie    { z-index: 3; }

/* Bottom half (example: kilt) */
.kilt {
  /*display: none;*/
  position: absolute;
  top: 35%;      /* adjust as needed */
  left: 50%;
  transform: translateX(-50%);
  width: 100%;   /* scale with baseBody */
  height: auto;
  z-index: 1;    /* between base and jacket */
}
</style>