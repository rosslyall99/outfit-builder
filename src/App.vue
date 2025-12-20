<template>
  <div class="outfit-builder">

    <!-- Left column: thumbnails -->
    <div class="thumbnails">

      <!-- Jacket section -->
      <div class="collapsible" :class="{ active: currentSection === 'jacket' }">
        <h3 class="section-heading collapsible-toggle" @click="toggleSection('jacket')">Jacket <span class="arrow">▼</span></h3>
        <div class="collapsible-content">
          <div class="section">
            <div class="thumbs">
              <div v-for="jacket in jackets"
                  :key="jacket.name"
                  class="thumb-container"
                  @click="selections.jacket = jacket"
                  :class="{ selected: selections.jacket.name === jacket.name }">
                <img :src="`${basePath}images/jacketSwatches/${jacket.swatch}`"
                    :alt="jacket.name" />
                <p class="thumb-label">{{ jacket.name }}</p>
              </div>
            </div>
          </div>
          <div class="collapsible-footer">
            <button class="nav-btn prev" @click="goToSection('shoes')">◀ Shoes</button>
            <button class="nav-btn next" @click="goToSection('shirt')">Shirt ▶</button>
          </div>
        </div>
      </div>

      <!-- Shirt section -->
      <div class="collapsible" :class="{ active: currentSection === 'shirt' }">
        <h3 class="section-heading collapsible-toggle" @click="toggleSection('shirt')">
          Shirt <span class="arrow">▼</span>
        </h3>
        <div class="collapsible-content">
          <div class="section">
            <div class="thumbs">
              <div v-for="shirt in shirts"
                  :key="shirt.name"
                  class="thumb-container"
                  @click="selections.shirt = shirt"
                  :class="{ selected: selections.shirt && selections.shirt.name === shirt.name }">
                <img :src="`${basePath}images/shirtSwatches/${shirt.swatch}`" :alt="shirt.name" />
                <p class="thumb-label">{{ shirt.name }}</p>
              </div>
            </div>
          </div>
          <div class="collapsible-footer">
            <button class="nav-btn prev" @click="goToSection('jacket')">◀ Jacket</button>
            <button class="nav-btn next" @click="goToSection('tie')">Tie ▶</button>
          </div>
        </div>
      </div>

      <!-- Tie section -->
      <div class="collapsible" :class="{ active: currentSection === 'tie' }">
        <h3 class="section-heading collapsible-toggle"
            @click="toggleSection('tie')">
          Tie <span class="arrow">▼</span>
        </h3>
        <div class="collapsible-content">
          <div class="section">
            <div class="thumbs">
              <div v-for="tie in ties"
                  :key="tie.name"
                  class="thumb-container"
                  @click="selections.tie = tie"
                  :class="{ selected: selections.tie.name === tie.name }">
                <img :src="`${basePath}images/tieSwatches/${tie.swatch}`" :alt="tie.name" />
                <p class="thumb-label">{{ tie.name }}</p>
              </div>
            </div>
          </div>
          <div class="collapsible-footer">
            <button class="nav-btn prev" @click="goToSection('shirt')">◀ Shirt</button>
            <button class="nav-btn next" @click="goToSection('kilt')">Kilt ▶</button>
          </div>
        </div>
      </div>

      <!-- Kilt section -->
      <div class="collapsible" :class="{ active: currentSection === 'kilt' }">
        <h3 class="section-heading collapsible-toggle"
            @click="toggleSection('kilt')">
          Kilt <span class="arrow">▼</span>
        </h3>
        <div class="collapsible-content">
          <div class="section">
            <div class="thumbs">
              <div v-for="kilt in kilts"
                  :key="kilt.name"
                  class="thumb-container"
                  @click="selections.kilt = kilt"
                  :class="{ selected: selections.kilt.name === kilt.name }">
                <img :src="`${basePath}images/kiltSwatches/${kilt.swatch}`" :alt="kilt.name" />
                <p class="thumb-label">{{ kilt.name }}</p>
              </div>
            </div>
          </div>
          <div class="collapsible-footer">
            <button class="nav-btn prev" @click="goToSection('tie')">◀ Tie</button>
            <button class="nav-btn next" @click="goToSection('sporran')">Sporran ▶</button>
          </div>
        </div>
      </div>

      <!-- Sporran section -->
      <div class="collapsible" :class="{ active: currentSection === 'sporran' }">
      <h3 class="section-heading collapsible-toggle" @click="toggleSection('sporran')">
        Sporran <span class="arrow">▼</span>
      </h3>
      <div class="collapsible-content">
        <div class="section">
          <div class="thumbs">
            <div v-for="sporran in sporrans"
                :key="sporran.name"
                class="thumb-container"
                @click="selections.sporran = sporran"
                :class="{ selected: selections.sporran && selections.sporran.name === sporran.name }">
              <img :src="`${basePath}images/sporranSwatches/${sporran.swatch}`" :alt="sporran.name" />
              <p class="thumb-label">{{ sporran.name }}</p>
            </div>
          </div>
        </div>
        <div class="collapsible-footer">
          <button class="nav-btn prev" @click="goToSection('kilt')">◀ Kilt</button>
          <button class="nav-btn next" @click="goToSection('socks')">Socks ▶</button>
        </div>
      </div>
      </div>
    
      <!-- Socks section -->
      <div class="collapsible" :class="{ active: currentSection === 'socks' }">
        <h3 class="section-heading collapsible-toggle" @click="toggleSection('socks')">
          Socks <span class="arrow">▼</span>
        </h3>
        <div class="collapsible-content">
          <div class="section">
            <div class="thumbs">
              <div v-for="socks in sockss"
                  :key="socks.name"
                  class="thumb-container"
                  @click="selections.socks = socks"
                  :class="{ selected: selections.socks && selections.socks.name === socks.name }">
                <img :src="`${basePath}images/sockSwatches/${socks.swatch}`" :alt="socks.name" />
                <p class="thumb-label">{{ socks.name }}</p>
              </div>
            </div>
          </div>
          <div class="collapsible-footer">
            <button class="nav-btn prev" @click="goToSection('sporran')">◀ Sporran</button>
            <button class="nav-btn next" @click="goToSection('shoes')">Shoes ▶</button>
          </div>
        </div>
      </div>

      <!-- Shoes section -->
      <div class="collapsible" :class="{ active: currentSection === 'shoes' }">
        <h3 class="section-heading collapsible-toggle" @click="toggleSection('shoes')">
          Shoes <span class="arrow">▼</span>
        </h3>
        <div class="collapsible-content">
          <div class="section">
            <div class="thumbs">
              <div v-for="shoes in shoess"
                  :key="shoes.name"
                  class="thumb-container"
                  @click="selections.shoes = shoes"
                  :class="{ selected: selections.shoes && selections.shoes.name === shoes.name }">
                <img :src="`${basePath}images/shoeSwatches/${shoes.swatch}`" :alt="shoes.name" />
                <p class="thumb-label">{{ shoes.name }}</p>
              </div>
            </div>
          </div>
          <div class="collapsible-footer">
            <button class="nav-btn prev" @click="goToSection('socks')">◀ Socks</button>
            <button class="nav-btn next" @click="goToSection('jacket')">Jacket ▶</button>
          </div>
        </div>
      </div>

      <!-- Face Section -->
       <div class="collapsible" :class="{ active: currentSection === 'face' }">
        <h3 class="section-heading collapsible-toggle" @click="toggleSection('face')">
          Face <span class="arrow">▼</span>
        </h3>

        <div class="collapsible-content">
          <div class="section">
            <div class="thumbs">
              <div v-for="face in faces"
                  :key="face.name"
                  class="thumb-container"
                  @click="selections.face = face"
                  :class="{ selected: selections.face && selections.face.name === face.name }">
                <img :src="`${basePath}images/${face.folder}/${face.swatch}`" :alt="face.name" />
                <p class="thumb-label">{{ face.name }}</p>
              </div>
              <div class="thumb-container upload-face" @click="$refs.faceUpload.click()">
                <div class="upload-thumb">
                  <span>+</span>
                </div>
                <p class="thumb-label">Upload</p>
              </div>
            </div>
            <div v-if="selections.face && selections.face.folder === null" class="face-adjust-controls">
              <div class="adjust-row">
                <button @click="nudgeY(-5)">⬆️</button>
              </div>
              <div class="adjust-row">
                <button @click="nudgeX(-5)">⬅️</button>
                <button @click="nudgeX(5)">➡️</button>
              </div>
              <div class="adjust-row">
                <button @click="nudgeY(5)">⬇️</button>
              </div>

              <div class="adjust-row">
                <button @click="adjustScale(0.025)">🔍➕</button>
                <button @click="adjustScale(-0.025)">🔍➖</button>
              </div>
            </div>
          </div>

          <div class="collapsible-footer">
            <button class="nav-btn prev" @click="goToSection('jacket')">◀ Jacket</button>
            <button class="nav-btn next" @click="goToSection('shirt')">Shirt ▶</button>
          </div>
        </div>

        <input
          type="file"
          accept="image/*"
          ref="faceUpload"
          @change="handleFaceUpload"
          style="display: none;"
        >
      </div>
    </div>

    <!-- Right column: preview -->
    <div class="preview">
      <div class="preview-stack">
        <img src="/images/baseBodynoHead.png" class="base-body" />
        <img v-if="selections.face" :src="faceSrc" :class="['face', selections.face.folder === null ? 'uploaded-face' : '']"   :style="uploadedFaceStyle"
 />
        <img v-if="selections.shirt" :src="`${basePath}images/shirtColors/${selections.shirt.preview}`" class="shirt" />
        <img v-if="selections.jacket" :src="`${basePath}images/jacketColors/${selections.jacket.preview}`" class="jacket" />
        <img v-if="selections.tie" :src="`${basePath}images/tieColors/${selections.tie.preview}`" class="tie" />
        <img v-if="selections.kilt" :src="`${basePath}images/kiltColors/${selections.kilt.preview}`" class="kilt" />
        <img v-if="selections.sporran" :src="`${basePath}images/${selections.sporran.preview}`" class="sporran" />
        <img v-if="selections.socks" :src="`${basePath}images/${selections.socks.preview}`" class="socks" />
        <img v-if="selections.shoes" :src="`${basePath}images/${selections.shoes.preview}`" class="shoes" />
      </div>
      <div class="section-buttons">
          <button class="section-button"@click="openModal('jacket', jackets, 'Jacket')">Jacket</button>
          <button class="section-button"@click="openModal('shirt', shirts, 'Shirt')">Shirt</button>
          <button class="section-button"@click="openModal('tie', ties, 'Tie')">Tie</button>
          <button class="section-button"@click="openModal('kilt', kilts, 'Kilt')">Kilt</button>
          <button class="section-button"@click="openModal('sporran', sporrans, 'Sporran')">Sporran</button>
          <button class="section-button"@click="openModal('socks', sockss, 'Socks')">Socks</button>
          <button class="section-button"@click="openModal('shoes', shoess, 'Shoes')">Shoes</button>
          <button class="section-button"@click="openModal('face', faces, 'Face')">Face</button>
      </div>
    </div>

    <!-- Mobile modal -->
    <div v-if="showModal" class="modal">
      <div class="modal-content">
        <button class="modal-close" @click="showModal = false">✕</button>
        <h3>{{ modalSectionLabel }}</h3>
        <div class="thumbs">
          <div v-for="option in modalOptions"
              :key="option.name"
              class="thumb-container"
              @click="selectOption(option)">
            <img :src="`${basePath}images/${option.folder}/${option.preview}`" :alt="option.name" />
            <p class="thumb-label">{{ option.name }}</p>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      currentSection: 'jacket', // default open section
      faces: [
        { name: 'Blonde', swatch: 'swatch-blonde.png', preview: 'face-blonde.png', folder: 'faceSwatches' },
        { name: 'Brown', swatch: 'swatch-brown.png', preview: 'face-brown.png', folder: 'faceSwatches' },
        { name: 'Black', swatch: 'swatch-black.png', preview: 'face-black.png', folder: 'faceSwatches' }
      ],
      jackets: [
        { name: 'Charcoal', swatch: 'swatch-charcoal.png', preview: 'jacket-charcoal.png', folder: 'jacketSwatches' },
        { name: 'Midnight Blue', swatch: 'swatch-midnightBlue.png', preview: 'jacket-midnightBlue.png', folder: 'jacketSwatches' },
        { name: 'Light Grey', swatch: 'swatch-lightGrey.png', preview: 'jacket-lightGrey.png', folder: 'jacketSwatches' },
        { name: 'Lovat Blue', swatch: 'swatch-lovatBlue.png', preview: 'jacket-lovatBlue.png', folder: 'jacketSwatches' },
        { name: 'Moss Green', swatch: 'swatch-mossGreen.png', preview: 'jacket-mossGreen.png', folder: 'jacketSwatches' },
        { name: 'Peat Brown', swatch: 'swatch-peatBrown.png', preview: 'jacket-peatBrown.png', folder: 'jacketSwatches' }
      ],
      kilts: [
        { name: 'Ancient Patriot', swatch: 'swatch-ancientPatriot.png', preview: 'kilt-ancientPatriot.png', folder: 'kiltSwatches' },
        { name: 'Beatson', swatch: 'swatch-beatson.png', preview: 'kilt-beatson.png', folder: 'kiltSwatches' },
        { name: 'Buchanan Hunting', swatch: 'swatch-buchanan.png', preview: 'kilt-buchanan.png', folder: 'kiltSwatches' },
        { name: 'Grey Slanj', swatch: 'swatch-greySlanj.png', preview: 'kilt-greySlanj.png', folder: 'kiltSwatches' },
        { name: 'Isle of Skye', swatch: 'swatch-isleOfSkye.png', preview: 'kilt-isleOfSkye.png', folder: 'kiltSwatches' },
        { name: 'Manx Hunting', swatch: 'swatch-manx.png', preview: 'kilt-manx.png', folder: 'kiltSwatches' },
        { name: 'Maple Leaf', swatch: 'swatch-mapleLeaf.png', preview: 'kilt-mapleLeaf.png', folder: 'kiltSwatches' },
        { name: 'Spirit of Glasgow', swatch: 'swatch-spiritOfGlasgow.png', preview: 'kilt-spiritOfGlasgow.png', folder: 'kiltSwatches' },
        { name: 'St Mirren FC', swatch: 'swatch-stMirren.png', preview: 'kilt-stMirren.png', folder: 'kiltSwatches' },
        { name: 'Weathered Patriot', swatch: 'swatch-weatheredPatriot.png', preview: 'kilt-weatheredPatriot.png', folder: 'kiltSwatches' }
      ],
      ties: [
        { name: 'Black', swatch: 'swatch-black.png', preview: 'tie-black.png', folder: 'tieSwatches' },
        { name: 'Champagne', swatch: 'swatch-champagne.png', preview: 'tie-champagne.png', folder: 'tieSwatches' },
        { name: 'Claret', swatch: 'swatch-claret.png', preview: 'tie-claret.png', folder: 'tieSwatches' },
        { name: 'Bottle Green', swatch: 'swatch-green.png', preview: 'tie-green.png', folder: 'tieSwatches' },
        { name: 'Dark Grey', swatch: 'swatch-grey.png', preview: 'tie-grey.png', folder: 'tieSwatches' },
        { name: 'Navy', swatch: 'swatch-navy.png', preview: 'tie-navy.png', folder: 'tieSwatches' },
        { name: 'Baby Pink', swatch: 'swatch-pink.png', preview: 'tie-pink.png', folder: 'tieSwatches' },
        { name: 'Purple', swatch: 'swatch-purple.png', preview: 'tie-purple.png', folder: 'tieSwatches' },
        { name: 'Dark Red', swatch: 'swatch-red.png', preview: 'tie-red.png', folder: 'tieSwatches' },
        { name: 'Silver', swatch: 'swatch-silver.png', preview: 'tie-silver.png', folder: 'tieSwatches' }
      ],
      selections: {
        face: null,
        jacket: { name: 'Charcoal', swatch: 'swatch-charcoal.png', preview: 'jacket-charcoal.png' },
        kilt: { name: 'Isle of Skye', swatch: 'swatch-isleOfSkye.png', preview: 'kilt-spiritOfGlasgow.png' },
        tie: { name: 'Silver', swatch: 'swatch-silver.png', preview: 'tie-silver.png' }
      },
      uploadedFaceTransform: {
        scale: 0.19,
        x: -5,
        y: 5
      },
      showModal: false,
      modalOptions: [],
      modalSection: null,
      modalSectionLabel: '',
      modalFolder: '' 
    }
  },

  computed: {
    basePath() {
      return import.meta.env.BASE_URL || '/'
    },
    faceSrc() {
      if (!this.selections.face) return null

      const preview = this.selections.face.preview

      // Uploaded image (data URL)
      if (preview.startsWith('data:')) {
        return preview
      }

      // Preloaded face — use its folder
      const folder = this.selections.face.folder || 'faceSwatches'
      return `${this.basePath}images/${folder}/${preview}`
    },
    uploadedFaceStyle() {
      if (!this.selections.face || this.selections.face.folder !== null) {
        return {}
      }

      const t = this.uploadedFaceTransform

      return {
        transform: `translate(${t.x}px, ${t.y}px) scale(${t.scale})`,
        transformOrigin: 'top center'
      }
    }
  },

  methods: {
    toggleSection(section) {
      this.currentSection = (this.currentSection === section ? null : section)
    },
    goToSection(section) {
      this.currentSection = section
    }, 
    openModal(section, options, label, folder) {
      this.modalSection = section
      this.modalOptions = options
      this.modalSectionLabel = label
      this.showModal = true
    },
    selectOption(option) {
      this.selections[this.modalSection] = option
      this.showModal = false
    },
    handleFaceUpload(event) {
      const file = event.target.files[0]
      if (!file) return

      const reader = new FileReader()

      reader.onload = e => {
        this.selections.face = {
          name: 'Uploaded Face',
          preview: e.target.result,
          folder: null
        }
        this.$refs.faceUpload.value = null
      }

      reader.readAsDataURL(file)
    },
    nudgeX(amount) {
      this.uploadedFaceTransform.x += amount
    },

    nudgeY(amount) {
      this.uploadedFaceTransform.y += amount
    },

    adjustScale(amount) {
      this.uploadedFaceTransform.scale = Math.max(0.1, this.uploadedFaceTransform.scale + amount)
    }
  }
}
</script>

<style>
#app {
  width: 100%;
  max-width: 100%;
  padding: 0rem 2rem;
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
  background-color: #f5f5f5;
  color: #a5a5a5;
  border: 1px solid #ccc;
  border-radius: 6px;
  display: flex;
  align-items: center;
  cursor: pointer;

  position: relative;   /* allow absolute positioning inside */
  justify-content: center; /* center the text */
  text-align: center;
}

.section-heading .arrow {
  position: absolute;
  right: 10px;   /* keep arrow on the right edge */
}


.section {
  background: #e4d8d8;
}

.collapsible.active {
  border: 1px solid #000;
  margin: 0;
}

.collapsible.active .section-heading {
  border: none;
  border-radius: 0;
  color: #000;
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

.collapsible-footer {
  display: flex;
  justify-content: space-between;
  background-color: #f9f9f9;
  border-top: 1px solid #ccc;
}

.nav-btn {
  display: flex;
  align-items: center;
  gap: 4px;
  background: none;
  border: none;
  color: #333;
  font-size: 0.9em;
  cursor: pointer;
}

.nav-btn:hover {
  color: #000;
}

.nav-btn:focus {
  outline: none;
  box-shadow: none;
  background-color: #d4d4d4;
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
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.preview-stack {
  position: relative;
  width: 40vw;               /* or 100% if you prefer full width */
  aspect-ratio: 3 / 4;       /* consistent proportions */
  max-height: 100vh;
  background: transparent;
}

/* All layers fill the stack */
.preview-stack img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: contain;
}

.uploaded-face {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: contain;
  transform-origin: top center;
}

.upload-face {
  cursor: pointer;
}

.upload-thumb {
  width: 80px;
  height: 80px;
  border: 2px dashed #aaa;
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
  color: #666;
  background-color: #f0f0f0;
}

.upload-thumb:hover {
  border-color: #000;
  color: #000;
}

.face-adjust-controls {
  margin-top: 10px;
  display: flex;
  flex-direction: column;
  gap: 6px;
  align-items: center;
}

.face-adjust-controls button {
  padding: 6px 10px;
  font-size: 1.2rem;
  border: 1px solid #aaa;
  background: #fafafa;
  border-radius: 6px;
  cursor: pointer;
  width: 48px;
  height: 48px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.adjust-row {
  display: flex;
  gap: 6px;
}

/* Layer order */
.base-body      { z-index: 1; }
.face           { z-index: 2; }
.uploaded-face  { z-index: 2; }
.shirt          { z-index: 2; }
.jacket         { z-index: 3; }
.tie            { z-index: 4; }
.kilt           { z-index: 2; }
.sporran        { z-index: 6; }
.socks          { z-index: 7; }
.shoes          { z-index: 8; }

/* Modal*/
.section-buttons {
  position: absolute;
  top: auto; 
  left: 10px;
  display: flex;
  flex-direction: column;
  gap: 8px;   /* space between buttons */
  z-index: 999;
}

.section-button {
  top: 10px;
  left: 10px;
  background: rgba(0,0,0,0.4);
  color: #fff;
  border: none;
  padding: 8px 12px;
  border-radius: 6px;
  z-index: 10;
}

.modal {
  position: fixed;
  top: 0; left: 0;
  width: 100vw; height: 100vh;
  background: rgba(0,0,0,0.6);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-content {
  position: relative;
  background: #fff;
  padding: 20px;
  border-radius: 8px;
  width: 90%;
  max-height: 80%;
  overflow-y: auto;
}

.modal-close {
  position: absolute;
  top: 0;
  right: 0;
  background: transparent;
  border: none;
  font-size: 1.5rem;
  color: #333;
  cursor: pointer;
}

.modal-close:hover {
  color: #000;
}

@media (max-width: 768px) {
  .thumbnails {
    display: none;
  }

  .preview-stack {
    position: relative;
    width: 100vw;
    height: 100vh;
    aspect-ratio: unset;
    max-height: none;
  }

  .section-buttons {
    display: flex;
  }
}

@media (min-width: 769px) {
  .section-buttons {
    display: none;
  }
}

</style>