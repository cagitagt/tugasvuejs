<template>
  <div id="app">
    <h1>{{ title }}</h1>

    <!-- Click Counter -->
    <div class="section counter">
      <h2>Click Counter</h2>
      <p class="counter-display">{{ count }}</p>
      <button @click="incrementCount" class="btn">Click</button>
    </div>

    <!-- Box Color Changer -->
    <div class="section color-changer">
      <h2>Box Color Changer</h2>
      <div :style="boxStyle" class="color-box"></div>
      <div class="color-buttons">
        <button @click="changeColor('lightpink')" class="btn btn-pink">Light Pink</button>
        <button @click="changeColor('lightblue')" class="btn btn-blue">Light Blue</button>
        <button @click="changeColor('lightgreen')" class="btn btn-green">Light Green</button>
      </div>
    </div>

    <!-- Image Carousel -->
    <div class="section carousel">
      <h2>Image Carousel</h2>
      <div class="carousel-wrapper">
        <img :src="images[currentImage]" alt="carousel image" class="carousel-image">
      </div>
      <div class="carousel-buttons">
        <button @click="prevImage" class="btn btn-carousel">Previous</button>
        <button @click="nextImage" class="btn btn-carousel">Next</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "Cagita's Vue.js Task",
      count: 0,
      boxColor: 'lightblue',
      images: [
        require('@/assets/5473158.jpg'),
        require('@/assets/5907011.jpg'),
        require('@/assets/6048943.jpg')
      ],
      currentImage: 0
    };
  },
  computed: {
    boxStyle() {
      return {
        width: '100px',
        height: '100px',
        backgroundColor: this.boxColor,
        borderRadius: '12px',
        transition: 'background-color 0.3s ease, transform 0.3s ease',
        boxShadow: '0px 6px 12px rgba(0,0,0,0.1)',
        margin: '20px auto',
        transform: 'scale(1)'
      };
    }
  },
  methods: {
    incrementCount() {
      this.count++;
    },
    changeColor(color) {
      this.boxColor = color;
    },
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    },
    prevImage() {
      this.currentImage = (this.currentImage - 1 + this.images.length) % this.images.length;
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;

}
body {
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, #ff9a9e, #fad0c4 40%, #fad0c4 40%, #fbc2eb 70%, #a18cd1 100%);
  font-family: 'Poppins', sans-serif;
}
#app {
  text-align: center;
  color: #333;
  max-width: 800px;
  padding: 40px;
}
h1 {
  font-size: 2em;
  color: #2d3436;
  margin-bottom: 30px;
  text-transform: uppercase;
  letter-spacing: 2px;
}
.section {
  margin-bottom: 50px;
  padding: 30px 200px;
  border-radius: 20px;
  border-color: #ffb74d;
  background-color: #f8f8fc6e;
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.05);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.section:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
}
.counter-display {
  font-size: 2.5em;
  font-weight: bold;
  margin: 20px 0;
  color: #000000;
}
.color-box {
  transition: transform 0.3s ease;
}
.color-box:hover {
  transform: scale(1.1);
}
.color-buttons {
  display: flex;
  justify-content: center;
  gap: 15px;
}
.carousel-wrapper {
  display: flex;
  justify-content: center;
  margin-bottom: 10px;
}
.carousel-image {
  margin-top: 15px;
  width: 300px;
  height: 200px;
  border-radius: 15px;
  object-fit: cover;
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.1);
}
.carousel-buttons {
  display: flex;
  justify-content: center;
  gap: 15px;
}
.btn {
  background-color: #ffb6c1;
  color: #333;
  padding: 12px 25px;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.3s ease;
}
.btn:hover {
  background-color: #ffffff;
  font-weight: bold;
  transform: translateY(-2px);
}
.btn-pink {
  background-color: lightpink;
}
.btn-blue {
  background-color: lightblue;
}
.btn-green {
  background-color: lightgreen;
}
.btn-carousel {
  background-color: #ffcc80;
}

</style>
