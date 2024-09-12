<template>
  <div id="app">
    <!-- Click Counter -->
    <div>
      <h2>Click Counter</h2>
      <button @click="incrementCounter">klik klik</button>
      <p>Kamu telah klik sebanyak {{ clickCount }} kali!</p>
    </div>

    <!-- Box Color Changer -->
    <div>
      <h2>Box Color Changer</h2>
      <div :style="{ backgroundColor: boxColor }" class="color-box"></div>
      <button @click="changeColor">Ganti warna</button>
    </div>

    <!-- Image Carousel -->
    <div>
      <h2>Image Carousel</h2>
      <div class="carousel">
        <img :src="images[currentImageIndex]" alt="Carousel Image" class="carousel-image" />
        <button @click="prevImage">Kembali</button>
        <button @click="nextImage">Lanjut</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // Click Counter
      clickCount: 0,

      // Box Color Changer
      boxColor: 'red',
      colors: ['red', 'green', 'blue', 'yellow'],

      // Image Carousel
      currentImageIndex: 0,
      images: [
  'https://picsum.photos/300/200?random=1',
  'https://picsum.photos/300/200?random=2',
  'https://picsum.photos/300/200?random=3',
],

    };
  },
  methods: {
    // Increment the click counter
    incrementCounter() {
      this.clickCount++;
    },

    // Change the color of the box
    changeColor() {
      const nextColorIndex =
        (this.colors.indexOf(this.boxColor) + 1) % this.colors.length;
      this.boxColor = this.colors[nextColorIndex];
    },

    // Move to the previous image in the carousel
    prevImage() {
      if (this.currentImageIndex === 0) {
        this.currentImageIndex = this.images.length - 1;
      } else {
        this.currentImageIndex--;
      }
    },

    // Move to the next image in the carousel
    nextImage() {
      if (this.currentImageIndex === this.images.length - 1) {
        this.currentImageIndex = 0;
      } else {
        this.currentImageIndex++;
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 50px;
}

.color-box {
  width: 150px;
  height: 150px;
  margin: 20px auto;
  transition: background-color 0.3s ease;
}

.carousel {
  margin: 20px auto;
}

.carousel-image {
  width: 300px;
  height: 200px;
  object-fit: cover;
}
</style>
