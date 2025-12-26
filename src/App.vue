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
            <button type="button" class="nav-btn prev" @click="goToSection('shoes')">◀ Shoes</button>
            <button type="button" class="nav-btn next" @click="goToSection('shirt')">Shirt ▶</button>
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
            <button type="button" class="nav-btn prev" @click="goToSection('jacket')">◀ Jacket</button>
            <button type="button" class="nav-btn next" @click="goToSection('tie')">Tie ▶</button>
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
            <button type="button" class="nav-btn prev" @click="goToSection('shirt')">◀ Shirt</button>
            <button type="button" class="nav-btn next" @click="goToSection('kilt')">Kilt ▶</button>
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
            <button type="button" class="nav-btn prev" @click="goToSection('tie')">◀ Tie</button>
            <button type="button" class="nav-btn next" @click="goToSection('sporran')">Sporran ▶</button>
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
          <button type="button" class="nav-btn prev" @click="goToSection('kilt')">◀ Kilt</button>
          <button type="button" class="nav-btn next" @click="goToSection('socks')">Socks ▶</button>
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
            <button type="button" class="nav-btn prev" @click="goToSection('sporran')">◀ Sporran</button>
            <button type="button" class="nav-btn next" @click="goToSection('shoes')">Shoes ▶</button>
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
            <button type="button" class="nav-btn prev" @click="goToSection('socks')">◀ Socks</button>
            <button type="button" class="nav-btn next" @click="goToSection('jacket')">Jacket ▶</button>
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
              <div class="thumb-container upload-face" @click="handleUploadClick">
                <div class="upload-thumb">
                  <span>+</span>
                </div>
                <p class="thumb-label">Upload</p>
              </div>
            </div>
          </div>

          <div class="collapsible-footer">
            <button type="button" class="nav-btn prev" @click="goToSection('jacket')">◀ Jacket</button>
            <button type="button" class="nav-btn next" @click="goToSection('shirt')">Shirt ▶</button>
          </div>
        </div>

        <input
          type="file"
          accept="image/*"
          :capture="useCamera ? 'user' : null"
          ref="faceUpload"
          @change="handleFaceUpload"
          style="display: none;"
        >
      </div>

      <!-- Face Adjust Overlay -->
      <div v-if="selections.face && selections.face.folder === null" class="face-adjust-overlay">
        <button type="button" @click="nudgeY(-4)">▲</button>
        <button type="button" @click="nudgeX(-4)">◀</button>
        <button type="button" @click="nudgeX(4)">▶</button>
        <button type="button" @click="nudgeY(4)">▼</button>
        <button type="button" @click="adjustScale(0.02)">＋</button>
        <button type="button" @click="adjustScale(-0.02)">－</button>
      </div>

      <!-- Bottom Bar - Price and Enquiry Button-->
      <div class="bottom-bar desktop-bottom-bar">
        <div class="price-display">£{{ totalPrice }}</div>
        <button type="button" class="section-button" @click="showEnquiryModal = true">Enquire</button>
      </div>
    </div>

    <!-- Mobile view section buttons -->
    <div class="section-buttons">
        <button type="button" class="section-button"@click="openModal('jacket', jackets, 'Jacket')">Jacket</button>
        <button type="button" class="section-button"@click="openModal('shirt', shirts, 'Shirt')">Shirt</button>
        <button type="button" class="section-button"@click="openModal('tie', ties, 'Tie')">Tie</button>
        <button type="button" class="section-button"@click="openModal('kilt', kilts, 'Kilt')">Kilt</button>
        <button type="button" class="section-button"@click="openModal('sporran', sporrans, 'Sporran')">Sporran</button>
        <button type="button" class="section-button"@click="openModal('socks', sockss, 'Socks')">Socks</button>
        <button type="button" class="section-button"@click="openModal('shoes', shoess, 'Shoes')">Shoes</button>
        <button type="button" class="section-button"@click="openModal('face', faces, 'Face')">Face</button>

        <!-- Face Adjust Overlay -->
        <div v-if="selections.face && selections.face.folder === null" class="face-adjust-overlay">
          <button type="button" @click="nudgeY(-4)">▲</button>
          <button type="button" @click="nudgeX(-4)">◀</button>
          <button type="button" @click="nudgeX(4)">▶</button>
          <button type="button" @click="nudgeY(4)">▼</button>
          <button type="button" @click="adjustScale(0.02)">＋</button>
          <button type="button" @click="adjustScale(-0.02)">－</button>
        </div>

        <div class="bottom-bar">
          <div class="price-display">£{{ totalPrice }}</div>
          <button type="button" class="section-button" @click="showEnquiryModal = true">Enquire</button>
        </div>
    </div>

    <!-- Outfit preview -->
    <div class="preview">
      <div class="preview-stack">
        <img src="/images/baseBodynoHead.png" class="base-body" />
        <img v-if="selections.face" :src="faceSrc" :class="['face', selections.face.folder === null ? 'uploaded-face' : '']"   :style="uploadedFaceStyle"/>
        <img v-if="selections.shirt" :src="`${basePath}images/shirtColors/${selections.shirt.preview}`" class="shirt" />
        <img v-if="selections.jacket" :src="`${basePath}images/jacketColors/${selections.jacket.preview}`" class="jacket" />
        <img v-if="selections.tie" :src="`${basePath}images/tieColors/${selections.tie.preview}`" class="tie" />
        <img v-if="selections.kilt" :src="`${basePath}images/kiltColors/${selections.kilt.preview}`" class="kilt" />
        <img v-if="selections.sporran" :src="`${basePath}images/${selections.sporran.preview}`" class="sporran" />
        <img v-if="selections.socks" :src="`${basePath}images/${selections.socks.preview}`" class="socks" />
        <img v-if="selections.shoes" :src="`${basePath}images/${selections.shoes.preview}`" class="shoes" />
      </div>
    </div>

    <!-- Mobile modal -->
    <div v-if="showModal" class="modal">
      <div class="modal-content">
        <button type="button" class="modal-close" @click="showModal = false">✕</button>
        <h3>{{ modalSectionLabel }}</h3>
        <div class="thumbs">
          <div v-for="option in modalOptions"
              :key="option.name"
              class="thumb-container"
              @click="selectOption(option)">
            <img :src="`${basePath}images/${option.folder}/${option.swatch}`" :alt="option.name" />
            <p class="thumb-label">{{ option.name }}</p>
          </div>
            <div v-if="modalSection === 'face'" class="thumb-container upload-face" @click="handleUploadClick">
            <div class="upload-thumb"><span>+</span></div>
            <p class="thumb-label">Upload</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Popup #1: Choose camera or upload -->
    <div v-if="showFaceSourceChoice" class="modal">
      <div class="modal-content">
        <button type="button" class="modal-close" @click="showFaceSourceChoice = false">✕</button>

        <h3>Select Photo Source</h3>

        <p>How would you like to add your face?</p>

        <div style="display: flex; flex-direction: column; gap: 12px; margin-top: 20px;">
          <button type="button" class="nav-btn" @click="chooseCamera">Take Photo with Camera</button>
          <button type="button" class="nav-btn" @click="chooseUpload">Upload from Phone</button>
        </div>
      </div>
    </div>

    <!-- Face photo instructions modal -->
    <div v-if="showFaceInstructions" class="modal">
      <div class="modal-content">
        <button type="button" class="modal-close" @click="showFaceInstructions = false">✕</button>
        <h3>How to take your photo</h3>
        <ul>
          <li>Stand in front of a plain white wall</li>
          <li>Face the camera straight on</li>
          <li>Ensure your head and hair are visible</li>
          <li>Avoid shadows or bright lights behind</li>
        </ul>

        <h3>Privacy notice</h3>
        <ul>
          <li>Your photo is not uploaded to any server</li>
          <li>It is processed only in your browser</li>
          <li>It will disappear when you close this page</li>
        </ul>

        <div style="display: flex; gap: 10px; justify-content: flex-end; margin-top: 15px;">
          <button type="button" class="nav-btn" @click="showFaceInstructions = false">Cancel</button>
          <button type="button" class="nav-btn" @click="continueToCamera">Continue</button>
        </div>
      </div>
    </div>

    <!-- Enquiry modal -->
    <div v-if="showEnquiryModal" class="modal">
      <div class="modal-content">

        <button type="button" class="modal-close" @click="showEnquiryModal = false">✕</button>

        <h3>Enquire About This Outfit</h3>

        <table class="enquiry-table">
          <tbody>
            <tr>
              <td class="label-cell">Function Date</td>
              <td><input type="date" v-model="enquiryForm.date" /></td>
            </tr>
            <tr>
              <td class="label-cell">Adult Hires</td>
              <td><input type="number" v-model="enquiryForm.adults" /></td>
            </tr>
            <tr>
              <td class="label-cell">Kids Hires</td>
              <td><input type="number" v-model="enquiryForm.kids" /></td>
            </tr>
            <tr>
              <td class="label-cell">Email Address</td>
              <td><input type="email" v-model="enquiryForm.email" /></td>
            </tr>
          </tbody>
        </table>

        <button 
          type="button" 
          class="section-button" 
          @click="submitEnquiry"
          :disabled="sending"
        >
          {{ sending ? 'Sending...' : 'Send Enquiry' }}
        </button>

        <p v-if="sendSuccess" style="color: green; margin-top: 10px;">
          Enquiry sent successfully!
        </p>

        <p v-if="sendError" style="color: red; margin-top: 10px;">
          Something went wrong — please try again.
        </p>

      </div>
    </div>
  </div>

  <!-- Debug log - currently not in use -->
  <pre id="debug-log"
      style="
        display:none;
        position:fixed;
        bottom:0;
        left:0;
        width:100%;
        max-height:30vh;
        overflow:auto;
        background:#000;
        color:#0f0;
        font-size:12px;
        padding:6px;
        z-index:99999;
      ">
  </pre>

</template>

<script>
  import {
  FilesetResolver,
  FaceDetector
} from "@mediapipe/tasks-vision"

  import emailjs from 'emailjs-com'

export default {
  data() {
    return {
      currentSection: 'jacket',
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
      shirts: [],
      sporrans: [],
      sockss: [],
      shoess: [],
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
      modalFolder: '',
      useCamera: false,
      faceDetector: null,
      uploadInProgress: false,
      showFaceSourceChoice: false,
      showFaceInstructions: false,
      debugDevice: '',
      PRICE_MAP: {
        base: 125,
        tartanPremiums: {'Beatson': 20},
        shoes: {'Brown': 10},
        sporran: {'Copper': 30},
        shirt: 20,
      },
      showEnquiryModal: false,
      enquiryForm: {
        date: '',
        adults: '',
        kids: '',
        email: ''
      },
      sending: false,
      sendSuccess: false,
      sendError: false,
    } 
  },

  computed: {
    basePath() {
      return import.meta.env.BASE_URL || '/'
    },

    faceSrc() {
      if (!this.selections.face) return null
      const preview = this.selections.face.preview
      if (preview.startsWith('data:')) return preview
      const folder = this.selections.face.folder || 'faceSwatches'
      return `${this.basePath}images/${folder}/${preview}`
    },

    uploadedFaceStyle() {
      if (!this.selections.face || this.selections.face.folder !== null) return {}
      const t = this.uploadedFaceTransform
      return {
        transform: `translate(${t.x}px, ${t.y}px) scale(${t.scale})`,
        transformOrigin: 'top center'
      }
    },

    isMobile() {
      const ua = navigator.userAgent || navigator.vendor || window.opera

      // True mobile devices
      if (/Android|iPhone|iPad|iPod/i.test(ua)) return true

      // Touchscreen laptops often report as mobile — filter them out
      if (navigator.maxTouchPoints && navigator.maxTouchPoints > 1) return false

      // Screen width fallback
      return window.innerWidth < 768
    },

    totalPrice() {
      let total = this.PRICE_MAP.base;

      // Tartan surcharge
      if (this.selections.kilt && this.selections.kilt.name) {
        const tartan = this.selections.kilt.name;
        if (this.PRICE_MAP.tartanPremiums[tartan]) {
          total += this.PRICE_MAP.tartanPremiums[tartan];
        }
      }

      // Shoes surcharge
      if (this.selections.shoes && this.selections.shoes.name) {
        const shoes = this.selections.shoes.name;
        if (this.PRICE_MAP.shoes[shoes]) {
          total += this.PRICE_MAP.shoes[shoes];
        }
      }

      // Sporran surcharge
      if (this.selections.sporran && this.selections.sporran.name) {
        const sporran = this.selections.sporran.name;
        if (this.PRICE_MAP.sporran[sporran]) {
          total += this.PRICE_MAP.sporran[sporran];
        }
      }

      // Shirt purchase
      if (this.selections.shirt && this.selections.shirt.name) {
        total += this.PRICE_MAP.shirt;
      }

      return total;
    }
  },

  methods: {
    toggleSection(section) {
      this.currentSection = (this.currentSection === section ? null : section)
    },

    goToSection(section) {
      this.currentSection = section
    },

    openModal(section, options, label) {
      this.modalSection = section
      this.modalOptions = options
      this.modalSectionLabel = label
      this.showModal = true
    },

    selectOption(option) {
      this.selections[this.modalSection] = option
      this.showModal = false
    },

    async handleFaceUpload(event) {
      if (this.uploadInProgress) {
        this.debug("Upload blocked — already in progress")
        return
      }
      this.uploadInProgress = true

      event.preventDefault()
      event.stopPropagation()

      const file = event.target.files[0]
      if (!file) return

      this.debug("File selected: " + file.name)
      this.showModal = false

      const reader = new FileReader()

      reader.onload = async e => {
        this.debug("FileReader loaded")

        const img = new Image()

        img.onload = async () => {
          this.debug("Image loaded: " + img.width + "x" + img.height)

          // Downscale for performance
          const MAX_SIZE = 512
          let srcW = img.width
          let srcH = img.height
          let scale = 1

          if (img.width > MAX_SIZE || img.height > MAX_SIZE) {
            scale = MAX_SIZE / Math.max(img.width, img.height)
            srcW = img.width * scale
            srcH = img.height * scale
          }

          // Draw to canvas (this is our single source)
          const inputCanvas = document.createElement("canvas")
          inputCanvas.width = srcW
          inputCanvas.height = srcH
          const ictx = inputCanvas.getContext("2d")
          ictx.drawImage(img, 0, 0, srcW, srcH)
          this.debug("Canvas prepared: " + srcW + "x" + srcH)

          let cropX, cropY, cropW, cropH

          // ⭐ MEDIA PIPE TASKS — HYBRID CROP
          if (this.faceDetector) {
            try {
              this.debug("Running MediaPipe FaceDetector…")
              
              await new Promise(r => setTimeout(r))
              const result = await this.faceDetector.detect(inputCanvas)

              if (result.detections.length > 0) {
                const det = result.detections[0]

                // Extract keypoints
                const keypoints = det.keypoints
                const xs = keypoints.map(p => p.x)
                const ys = keypoints.map(p => p.y)

                const minX = Math.min(...xs)
                const maxX = Math.max(...xs)
                const minY = Math.min(...ys)
                const maxY = Math.max(...ys)

                const boxW = maxX - minX
                const boxH = maxY - minY

                const padding = 0.15

                // Keypoint crop
                cropX = Math.max(0, minX - boxW * padding)
                cropY = Math.max(0, minY - boxH * padding)
                cropW = Math.min(inputCanvas.width - cropX, boxW * (1 + padding * 2))
                cropH = Math.min(inputCanvas.height - cropY, boxH * (1 + padding * 2))

                this.debug("Crop (Keypoints): " + [cropX, cropY, cropW, cropH].join(", "))

                // ⭐ Fallback if keypoint crop is too small
                if (cropW < 50 || cropH < 50) {
                  this.debug("Keypoint crop too small — falling back to bounding box")

                  const box = det.boundingBox

                  cropX = Math.max(0, box.originX - box.width * padding)
                  cropY = Math.max(0, box.originY - box.height * padding)
                  cropW = Math.min(inputCanvas.width - cropX, box.width * (1 + padding * 2))
                  cropH = Math.min(inputCanvas.height - cropY, box.height * (1 + padding * 2))

                  this.debug("Fallback crop (bounding box): " + [cropX, cropY, cropW, cropH].join(", "))
                }

              } else {
                this.debug("No face detected — using center crop")
                const size = Math.min(inputCanvas.width, inputCanvas.height)
                cropX = (inputCanvas.width - size) / 2
                cropY = (inputCanvas.height - size) / 2
                cropW = size
                cropH = size
              }
            } catch (err) {
              this.debug("MediaPipe detection error: " + err)
              const size = Math.min(inputCanvas.width, inputCanvas.height)
              cropX = (inputCanvas.width - size) / 2
              cropY = (inputCanvas.height - size) / 2
              cropW = size
              cropH = size
            }
          } else {
            this.debug("FaceDetector not loaded — using center crop")
            const size = Math.min(inputCanvas.width, inputCanvas.height)
            cropX = (inputCanvas.width - size) / 2
            cropY = (inputCanvas.height - size) / 2
            cropW = size
            cropH = size
          }

          // ⭐ ADD HEADROOM ABOVE THE FACE
          const headroom = cropH * 0.35
          const neckroom = cropH * 0.15
          cropY = Math.max(0, cropY - headroom)
          cropH = Math.min(inputCanvas.height - cropY, cropH + headroom + neckroom)

          // ⭐ Clamp final crop to valid region
          cropX = Math.max(0, Math.min(cropX, inputCanvas.width - 1))
          cropY = Math.max(0, Math.min(cropY, inputCanvas.height - 1))
          cropW = Math.max(50, Math.min(cropW, inputCanvas.width - cropX))
          cropH = Math.max(50, Math.min(cropH, inputCanvas.height - cropY))

          this.debug("FINAL CROP BOX: " + [cropX, cropY, cropW, cropH].join(", "))

          // ⭐ DRAW CROPPED IMAGE
          try {
            const outCanvas = document.createElement("canvas")
            outCanvas.width = Math.round(cropW)
            outCanvas.height = Math.round(cropH)

            const octx = outCanvas.getContext("2d")
            octx.drawImage(
              inputCanvas,
              cropX, cropY, cropW, cropH,
              0, 0, outCanvas.width, outCanvas.height
            )

            const cropped = outCanvas.toDataURL("image/png")
            this.debug("Cropped image created: " + (cropped ? "yes" : "NO"))
            this.debug("CROPPED LENGTH: " + cropped.length)

            // ⭐ UPDATE FACE SELECTION
            this.selections.face = {
              name: "Uploaded Face",
              preview: cropped,
              folder: null
            }

            this.debug("Face selection updated")

            // Reset transform defaults
            this.uploadedFaceTransform = {
              scale: 0.19,
              x: -5,
              y: 5
            }

            this.debug("Transform reset")

            this.$refs.faceUpload.value = null
            this.debug("Upload input cleared")
          } catch (err) {
            this.debug("Error during crop/toDataURL/update: " + err)
          }

          this.uploadInProgress = false
        }

        img.src = e.target.result
        this.debug("Image src set")
      }

      reader.readAsDataURL(file)
      this.debug("FileReader started")
    },

    nudgeX(amount) {
      this.uploadedFaceTransform.x += amount
    },

    nudgeY(amount) {
      this.uploadedFaceTransform.y += amount
    },

    adjustScale(amount) {
      this.uploadedFaceTransform.scale = Math.max(0.1, this.uploadedFaceTransform.scale + amount)
    },

    chooseCamera() {
      this.useCamera = true
      this.showFaceSourceChoice = false
      this.showFaceInstructions = true
    },

    chooseUpload() {
      this.useCamera = false
      this.showFaceSourceChoice = false
      this.$refs.faceUpload.click()
    },

    continueToCamera() {
      this.showFaceInstructions = false
      this.$refs.faceUpload.click()
    },

    async initFaceDetector() {
      this.debug("Loading MediaPipe FaceDetector…")

      try {
        const vision = await FilesetResolver.forVisionTasks(
          "https://cdn.jsdelivr.net/npm/@mediapipe/tasks-vision/wasm"
        )

        this.faceDetector = await FaceDetector.createFromOptions(vision, {
          baseOptions: {
            modelAssetPath:
              "https://storage.googleapis.com/mediapipe-models/face_detector/blaze_face_short_range/float16/1/blaze_face_short_range.tflite"
          },
          runningMode: "IMAGE",
          minDetectionConfidence: 0.5
        })

        this.debug("MediaPipe FaceDetector loaded")
      } catch (err) {
        this.debug("Failed to load MediaPipe FaceDetector: " + err)
        this.faceDetector = null
      }
    },

    debug(msg) {
      if (/Android/i.test(navigator.userAgent)) return
      const el = document.getElementById("debug-log")
      if (el) el.innerText += msg + "\n"
    },

    handleUploadClick() {
      if (this.isMobile) {
        // Mobile → show camera/upload choice
        this.showFaceSourceChoice = true
      } else {
        // Desktop → go straight to file picker
        this.$refs.faceUpload.click()
      }
    },

    cleanupBeforeReload() {
      this.debug("Cleaning up stale listeners and detectors…")

      // Reset file input completely
      if (this.$refs.faceUpload) {
        this.$refs.faceUpload.value = null
      }

      // Kill any stale detector instance
      if (this.faceDetector && this.faceDetector.close) {
        try { this.faceDetector.close() } catch(e) {}
      }

      this.faceDetector = null

      // Clear any leftover canvases (Android sometimes keeps them alive)
      const canvases = document.querySelectorAll("canvas")
      canvases.forEach(c => {
        try { c.width = 0; c.height = 0 } catch(e) {}
      })
    },

    async submitEnquiry() {
      this.sending = true
      this.sendSuccess = false
      this.sendError = false

      try {
        const payload = {
          date: this.enquiryForm.date,
          adults: this.enquiryForm.adults,
          kids: this.enquiryForm.kids,
          email: this.enquiryForm.email,

          jacket: this.selections.jacket?.name || '',
          shirt: this.selections.shirt?.name || '',
          tie: this.selections.tie?.name || '',
          kilt: this.selections.kilt?.name || '',
          sporran: this.selections.sporran?.name || '',
          socks: this.selections.socks?.name || '',
          shoes: this.selections.shoes?.name || '',
          face: this.selections.face?.name || ''
        }

        await emailjs.send(
          "service_tk8jn8g",
          "template_75o2wq8",
          payload,
          "YoH7CX3KASZqKB6Hs"
        )

        this.sendSuccess = true
        this.showEnquiryModal = false

      } catch (err) {
        console.error(err)
        this.sendError = true
      }

      this.sending = false
    }
  },

  mounted() {
    this.initFaceDetector()
    this.cleanupBeforeReload()
    this.initFaceDetector()
    emailjs.init("YoH7CX3KASZqKB6Hs")
  },

  beforeUnmount() {
    this.cleanupBeforeReload()
  },
}
</script>

<style>
#app {
  width: 100%;
  max-width: 100%;
  padding: 0px;
}

body {
  background-color: white;
  color: #000;
  padding: 0px;
}

h3 {
  margin: 0;
}

.outfit-builder {
  display: flex;
  width: 100%;
  height: 100vh;
  padding: 0px;
}

.collapsible {
  border-radius: 6px;
  overflow: hidden;
}

.section-heading {
  padding: 8px;
  background: rgba(10, 19, 104, 0.4);
  color: #ffffff;
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
  background: rgb(255, 255, 255);
}

.collapsible.active {
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
  padding: 1%;
  gap:1%;
  width: 40%;
  display: flex;
  position: relative;
  flex-direction: column;
  background: rgba(10, 19, 104, 0.2);
}

.thumbs {
  display: grid;
  padding: 1%;
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
  width: 80%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  position: relative;
  overflow-y: auto;
  box-sizing: border-box;
}

@media (min-width: 768px) {
  .preview {
    width: 60%;
    margin-left: auto;
  }
}

.preview-stack {
  position: relative;
  width: 100%;
  aspect-ratio: 3 / 4;
  max-height: 100%;
  margin: 0 auto;          /* centres horizontally */
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

.face-adjust-overlay {
  display: flex;
  border-radius: 4px;
  z-index: 999;
  background: rgba(10,10,104, 0.4);
  padding: 8px;
  justify-content: space-between;
  box-sizing: border-box;  
  gap: 8px;
}

@media (max-width: 768px) {
  .face-adjust-overlay {
    flex-direction: column;
    top: 0px;
    right: 0px;
  }
}

.face-adjust-overlay button {
  width: 100%;
  height: 2.5rem;
  font-size: 1rem;
  border: 1px solid #fff;
  background: rgba(10, 19, 104, 0);
  border-radius: 4px;
  cursor: pointer;
}

.face-adjust-overlay button:hover {
  background: rgba(10, 19, 104, 0.6);
}

/* Layer order */
.base-body      { z-index: 1; }
.face           { z-index: 0; }
.uploaded-face  { z-index: 0; }
.shirt          { z-index: 2; }
.jacket         { z-index: 3; }
.tie            { z-index: 4; }
.kilt           { z-index: 2; }
.sporran        { z-index: 6; }
.socks          { z-index: 7; }
.shoes          { z-index: 8; }

/* Modal*/
.section-buttons {
  width: 20%;
  min-width: 100px;
  position: relative;
  top: 0px;
  left: 0px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  gap: 8px;
  padding: 8px;
  background: rgba(10, 19, 104, 0.2);
  z-index: 999;
  border-radius: 4px;
  height: 100vh;
  box-sizing: border-box;
}

@media (min-width: 769px) {
  .section-buttons {
    display: none;
  }
}

.section-button {
  top: 10px;
  left: 10px;
  background: rgba(10, 19, 104, 0.4);
  color: #fff;
  border: none;
  padding: 8px;
  border-radius: 4px;
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
  padding: 0px 0px 16px 0px;
  border-radius: 8px;
  width: 90%;
  max-height: 80%;
  transform: none !important;
  overflow: visible !important;
}

.modal-close {
  position: absolute;
  padding: 0px;
  top: 8px;
  right: 16px;
  background: transparent;
  border: none;
  font-size: 1.5rem;
  color: #ffffff;
  cursor: pointer;
}

.modal-close:hover {
  color: #000;
}

.modal .thumbs {
  display: grid !important;
  grid-template-columns: repeat(auto-fill, minmax(80px, 1fr));
  gap: 8px;
  width: 100%;
  padding: 16px;
  box-sizing: border-box;
  justify-items: center;
}

.modal-content h3 {
  background: rgba(10, 19, 104, 0.6);
  color: white;
  margin: 0;
  padding: 12px 16px;
  text-align: center;
  font-size: 1.2rem;
  font-weight: 600;
  width: 100%;
  box-sizing: border-box;
  border-top-left-radius: 6px;
  border-top-right-radius: 6px;
}

li {
  text-align: left;
}

.bottom-bar {
  margin-top: auto;
  display: flex;
  flex-direction: column;
  gap: 8px;
  z-index: 999;
  border-radius: 4px;
}

.price-display {
  font-size: 24px;
  font-weight: bold;
  color: #fff;
  border-radius: 4px;
  background: rgba(78, 85, 153, 1);
}

.enquiry-table {
  width: 100%;
  border-collapse: collapse;
  margin: 16px 0;
}

.enquiry-table td {
  padding: 8px 12px;
  vertical-align: middle;
}

.label-cell {
  text-align: right;
  font-weight: 600;
  color: #333;
  width: 40%;
  white-space: nowrap;
}

.enquiry-table input {
  width: 100%;
  padding: 8px 12px;
  color: #000;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  background: white;
  box-sizing: border-box;
  appearance: auto;
}

input[type="date"]::-webkit-calendar-picker-indicator {
  filter: brightness(0) saturate(100%);
}

input[type="number"] {
  background-color: white !important;
  color-scheme: light !important;
  color: #000 !important;
}

.enquiry-table input:focus {
  border-color: #0a1368;
  outline: none;
  box-shadow: 0 0 0 2px rgba(10, 19, 104, 0.2);
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

}

@media (min-width: 769px) {
  .section-buttons {
    display: none;
  }

  .face-adjust-overlay {
    display: flex;
  }
}

</style>