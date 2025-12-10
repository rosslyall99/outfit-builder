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
              :src="`${basePath}images/${jacket.swatch}`"
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
    </div>

    <!-- Right column: preview -->
    <div class="preview">
  <div class="preview-stack">
    <img :src="`${basePath}images/baseBody.png`" class="base-body" />
    <img :src="`${basePath}images/${selections.jacket.preview}`" class="jacket" />
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
        { name: 'Charcoal', swatch: '/jacketSwatches/swatch-charcoal.png', preview: '/jacketColors/jacket-charcoalGen.png' },
        { name: 'Midnight Blue', swatch: '/jacketSwatches/swatch-midnightBlue.png', preview: '/jacketColors/jacket-midnightBlueGen.png' },
        { name: 'Light Grey', swatch: '/jacketSwatches/swatch-lightGrey.png', preview: '/jacketColors/jacket-lightGreyGen.png' },
        { name: 'Lovat Blue', swatch: '/jacketSwatches/swatch-lovatBlue.png', preview: '/jacketColors/jacket-lovatBlueGen.png' },
        { name: 'Moss Green', swatch: '/jacketSwatches/swatch-mossGreen.png', preview: '/jacketColors/jacket-mossGreenGen.png' },
        { name: 'Peat Brown', swatch: '/jacketSwatches/swatch-peatBrown.png', preview: '/jacketColors/jacket-peatBrownGen.png' }
      ],
      kilts: [
        { name: 'Ancient Patriot', swatch: 'swatch-ancientPatriot.png', preview: 'kilt-ancientPatriot.png' },
        { name: 'Beatson', swatch: 'swatch-beatson.png', preview: 'kilt-beatson.png' },
        { name: 'Buchanan Hunting', swatch: 'swatch-buchanan.png', preview: 'kilt-buchanan.png' },
        { name: 'Grey Slanj', swatch: 'swatch-greySlanj.png', preview: 'kilt-greySlanj.png' },
        { name: 'Isle of Skye', swatch: 'swatch-isleOfSkye.png', preview: 'kilt-isleOfSkye.png' },
        { name: 'Manx Hunting', swatch: 'swatch-manx.png', preview: 'kilt-manx.png' },
        { name: 'Maple Leaf', swatch: 'swatch-mapleLeaf.png', preview: 'kilt-mapleLeaf.png' },
        { name: 'Spirit of Glasgow', swatch: 'swatch-spiritOfGlasgow.png', preview: 'kilt-spiritOfGlasgow.png' },
        { name: 'St Mirren FC', swatch: 'swatch-stMirren.png', preview: 'kilt-stMirren.png' },
        { name: 'Weathered Patriot', swatch: 'swatch-weatheredPatriot.png', preview: 'kilt-weatheredPatriot.png' },
      ],
      selections: {
        jacket: { name: 'Charcoal', swatch: 'swatch-charcoal.png', preview: 'jacket-charcoal.png' },
        kilt: { name: 'Isle of Skye', swatch: 'swatch-isleOfSkye.png', preview: 'kilt-isleOfSkye.png' }
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

.thumbs {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  justify-content: flex-start;
}

.thumbs img {
  width: 100px;
  height: 100px;
  object-fit: cover;
  cursor: pointer;
  border: 2px solid transparent;
  border-radius: 4px;
}

.thumbnails {
  display: grid;
  grid-template-rows: repeat(8, 1fr);
}

.section {
  padding: 10px;
  background: #f9f9f9;
  border-radius: 6px;
  border: 1px solid #ddd;
}

.preview {
  position: relative;
  height: auto;
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

.preview-stack img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: auto;
}

.thumbs img.selected {
  border-color: #000;
}

.preview {
  position: relative;
  height: 800px;
}

.kilt {
  position: absolute;
  top: 35%;
  left: 52%;
  transform: translateX(-50%);
  width: 300px;
  z-index: 1; /* lower layer */
}

.jacket {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 300px;
  z-index: 2; /* higher layer */
}

.thumb-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  cursor: pointer;
}

.thumb-container img {
  width: 100px;
  height: 100px;
  object-fit: cover;
  border: 2px solid transparent;
  border-radius: 4px;
}

.thumb-container.selected img {
  border-color: #000;
}

.thumb-label {
  margin-top: 5px;
  font-size: 14px;
  color: #333;
}

.base-body {
  width: 100%;
  height: auto;
  display: block;
  z-index: 0; /* bottom layer */
  position: relative; /* acts as anchor */
}

.jacket {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 300px;
  z-index: 2; /* above base */
}

.kilt {
  position: absolute;
  top: 35%;
  left: 52%;
  transform: translateX(-50%);
  width: 300px;
  z-index: 1; /* between base and jacket */
}
</style>