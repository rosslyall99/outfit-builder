<template>
  <div class="outfit-builder">
    <!-- Jacket thumbnails -->
    <h3>Select a Jacket</h3>
    <div class="thumbs">
      <img
        v-for="jacket in jackets"
        :key="jacket"
        :src="`${basePath}images/jacket-${jacket}.png`"
        :alt="jacket"
        @click="selections.jacket = jacket"
        :class="{ selected: selections.jacket === jacket }"
      />
    </div>

    <!-- Kilt thumbnails -->
    <h3>Select a Kilt</h3>
    <div class="thumbs">
      <img
        v-for="kilt in kilts"
        :key="kilt"
       :src="`${basePath}images/kilt-${kilt}.png`"
        :alt="kilt"
        @click="selections.kilt = kilt"
        :class="{ selected: selections.kilt === kilt }"
      />
    </div>

    <!-- Preview area -->
    <div class="preview">
      <img :src="`${basePath}images/kilt-${selections.kilt}.png`" class="kilt" />
      <img :src="`${basePath}images/jacket-${selections.jacket}.png`" class="jacket" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      jackets: ['charcoal', 'midnightBlue', 'lightGrey'],
      kilts: ['ancientPatriot', 'isleOfSkye', 'greySlanj'],
      selections: {
        jacket: 'charcoal',
        kilt: 'isleOfSkye'
      }
    }
  },
  computed: {
    basePath() {
      return import.meta.env.BASE_URL
    }
  }
}
</script>

<style>
body {
  background-color: white;
  color: #000;
}

.outfit-builder {
  max-width: 900px;
  margin: auto;
  text-align: center;
}

.thumbs {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-bottom: 20px;
}

.thumbs img {
  width: 100px;
  height: 100px;
  object-fit: cover;
  cursor: pointer;
  border: 2px solid transparent;
  border-radius: 4px;
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
  top: 300px;
  left: 50%;
  transform: translateX(-50%);
  width: 300px;
}

.jacket {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 300px;
}
</style>