<template>
  <div class="outfit-builder">

    <!-- Left column: thumbnails -->
    <div class="thumbnails">

      <!-- ✅ Jacket section (now collapsible) -->
      <div class="collapsible">
        <h3 class="section-heading collapsible-toggle">Select a Jacket<span class="arrow">▼</span></h3>

        <div class="collapsible-content">
          <div class="section">
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
        </div>
      </div>

      <!-- ✅ Kilt section (already collapsible, cleaned up) -->
      <div class="collapsible">
        <h3 class="section-heading collapsible-toggle">Select a Kilt<span class="arrow">▼</span></h3>

        <div class="collapsible-content">
          <div class="section">
            <div class="thumbs">
              <div
                v-for="kilt in kilts"
                :key="kilt.name"
                class="thumb-container"
                @click="selections.kilt = kilt"
                :class="{ selected: selections.kilt.name === kilt.name }"
              >
                <img :src="`${basePath}images/${kilt.swatch}`" :alt="kilt.name" />
                <p class="thumb-label">{{ kilt.name }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- ✅ Tie section (now collapsible) -->
      <div class="collapsible">
        <h3 class="section-heading collapsible-toggle">Select a Tie<span class="arrow">▼</span></h3>

        <div class="collapsible-content">
          <div class="section">
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
  },

  mounted() {
    document.querySelectorAll('.collapsible-toggle').forEach(toggle => {
      toggle.addEventListener('click', () => {
        toggle.parentElement.classList.toggle('active');
      });
    });
  }
}
</script>

<style>
#app {
  width: 100%;
  max-width: 100%;
}

body {
  background-color: white;
  color: #000;
}

h3 {
  margin: 0;
}

.outfit-builder {
  display: grid;
  grid-template-columns: 1fr auto;
  width: 100%;
  height: 100vh;
}

.collapsible {
  border: 1px solid transparent;
  border-radius: 6px;
  overflow: hidden;
}

.section-heading {
  padding: 0.5%;
  background-color: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 1px solid #000;
  border-radius: 6px;
  cursor: pointer;
}

.section {
  background: #e4d8d8;
  border-radius: 6px;
}

.collapsible.active {
  border: 1px solid #000;
  margin: 0;
}

.collapsible.active .section-heading {
  border: none;
  border-radius: 0;
}

.collapsible-toggle {
  cursor: pointer;
}

.collapsible-content {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.5s ease;
}

.collapsible.active .collapsible-content {
  max-height: 1000px;
}

.collapsible.active .arrow {
  transform: rotate(180deg);
}

.arrow {
  transition: transform 0.5s ease;
}

/* Thumbnail sections */
.thumbnails {
  display: flex;
  flex-direction: column;
  gap: 1%;
  margin-right: 1.5%;
}

.thumbs {
  display: grid;
  padding: 0.5%;
  grid-template-columns: repeat(auto-fill, minmax(80px, 1fr));
  gap: 0.5%;
}

.thumb-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  cursor: pointer;
}

.thumb-container img,
.thumbs img {
  width: 80px;
  height: 80px;
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
  margin: 1%;
  font-size: 0.8em;
  font-weight: 500;
  color: #333;
  white-space: normal;
  max-width: 80px;
  text-align: center;
}

/* Preview area */
.preview {
  height: 100vh;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.preview-stack {
  max-height: 100vh;           /* never taller than viewport */
  max-width: 100vw;            /* never wider than viewport */
  width: auto;
  height: auto;
  aspect-ratio: 3 / 4;
  object-fit: contain;         /* ensures full image fits */
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
  position: absolute;
  top: 0%;      /* adjust as needed */
  left: 50%;
  transform: translateX(-50%);
  width: 100%;   /* scale with baseBody */
  height: auto;
  z-index: 1;    /* between base and jacket */
}
</style>