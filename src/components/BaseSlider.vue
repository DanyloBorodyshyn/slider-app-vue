<template>
  <div class="swiper-container">
    <swiper @slideChange="onSlideNextEnd" rotate @swiper="onSwiper" :effect="'cards'" :modules="modules" loop>
      <swiper-slide v-for="(slide, index) in slides" :key="index" class="rounded"
        :style="{ backgroundColor: slide.color }">
        <div class="slide-content">
          <img class="star-image" src="../assets/images/star.svg" alt="Slide Image">
          <p class="subtitle">Lorem ipsum dolor sit amet
          <div class="ellipse header_ellipse"></div>
          </p>

          <p class="title">LOREM IPSUM</p>
          <p class="text-border title">LOREM IPSUM DOLOR -</p>
          <p class="centered-text stay">Lorem </p>
          <p class="centered-text header-end-text">ipsum ! </p>
          <p class="quote">Lorem ipsum dolor sit amet, consectetur adipiscing elit</p>
          <img class="dog-image" src="../assets/images/swiper_image.png" alt="Slide Image">
          <div class="white-ellipse"></div>
          <div class="ellipse grey-ellipse"></div>
          <div class="pagination">
            <p>{{ (index + 1) + '/' + (slides.length) }}</p>
          </div>
        </div>
      </swiper-slide>
    </swiper>
    <button @click="swiperUse.slideNext()" class="navigation-button"></button>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { Swiper, SwiperSlide } from 'swiper/vue';
import { EffectCards } from 'swiper/modules';
import 'swiper/css';
import 'swiper/css/effect-cards';

const modules = [EffectCards]
const swiperUse = ref(null)
const slides = ref([
  { color: '#008080' },
  { color: '#004C4C' },
  { color: '#002626' },
  { color: '#001313' }
]);

const onSwiper = (swiperData) => {
  swiperData.allowTouchMove = false
  swiperUse.value = swiperData
}

</script>

<style scoped>
.rounded,
.swiper-slide {
  border: 1px solid #000;
  border-top-right-radius: 80px;
  border-bottom-right-radius: 80px;
  box-shadow: 0 3px 5px 1px gray;
}

.title {
  font-size: 60px;
  font-weight: 700;
}

.ellipse {
  width: 465px;
  height: 240px;
  border-radius: 50%;
  background: #AFB3B4;
}

.white-ellipse {
  width: 465px;
  height: 240px;
  border-radius: 50%;
  background: none;
  border: 1px solid #fff;
  transform: rotate(-140deg);
  position: absolute;
  z-index: 4;
  bottom: 40%;
  right: 10%;
}

.grey-ellipse {
  position: absolute;
  transform: rotate(-15deg);
  bottom: 19%;
  right: 12.4%;
}

.swiper-container {
  position: relative;
  width: 100vw;
}

.swiper-button-next {
  position: absolute;
  background: none;
  background-image: url('../assets/images/next_arrow.svg') !important;
  background-repeat: no-repeat;
  background-position: center;
  z-index: 5;
}

.slide-content {
  position: relative;
  min-height: 710px;
  padding: 20px 150px;
}

.slide-content p {
  margin-top: 0;
  margin-bottom: 0;
}

.slide-content .subtitle {
  margin-bottom: 40px;
}

.slide-content .quote {
  margin-top: 40px;
}

.header_ellipse {
  position: absolute;
  z-index: -1;
  content: '';
  top: -205px;
  left: -150px;
  transform: rotate(13deg);
}

.subtitle {
  z-index: 3;
  position: relative;
  font-size: 14px;
  font-weight: 500;
  text-transform: uppercase;
  margin-bottom: 60px;
}

.subtitle {
  text-shadow: 2px 1px 3px #000;
}

.slide-content h1 {
  color: white;
}

.slide-content p {
  color: white;
}

.text-border {
  -webkit-text-stroke: 2px black;
  color: #fff;
  padding-left: 45px;
  font-weight: 400;
}

.centered-text {
  text-transform: uppercase;
  font-size: 60px;
  margin-left: 300px;
}

.header-end-text {
  margin-left: 143px;
  margin-bottom: 60px;
}

.quote {
  text-transform: uppercase;
  font-weight: 500;
  font-size: 15px;
  max-width: 280px;
  margin-left: 280px;
  margin-top: 40px;
}

.navigation-button {
  position: absolute;
  width: 120px;
  height: 120px;
  background: none;
  border: none;
  background-image: url('../assets/images/next_arrow.svg');
  right: 8%;
  top: 40%;
  z-index: 3;
}

.dog-image {
  position: absolute;
  bottom: 5px;
  right: 20%;
  z-index: 5;
}

.star-image {
  position: absolute;
  left: 0;
  top: 50%;
  z-index: 5;
}

.pagination {
  display: none;
}

@media (max-width:1400px) {
  .quote {
    margin-left: 200px;
  }

  .title,
  .centered-text {
    font-size: 40px;
  }
}

@media (max-width:1200px) {
  .quote {
    margin-left: 200px;
  }

  .title,
  .centered-text {
    font-size: 40px;
  }

  .pagination {
    position: absolute;
    bottom: 30px;
    left: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    width: 100px;
    height: 50px;
    border: 1px solid #fff;
  }

  .text-border {
    -webkit-text-stroke: 0px black;
  }

  .slide-content {
    min-height: 900px;
    padding: 20px 80px;
  }

  .header_ellipse {
    right: 100px;
    left: initial;
  }

  .subtitle {
    text-align: right;
    padding-right: 205px;
  }

  .star-image {
    left: -55px;
    height: 140px;
    width: 140px;
    top: 240px;
  }
}

@media (max-width: 800px) {
  .slide-content .quote {
    margin-top: 0;
    font-size: 15px;
    margin-left: 55%;
  }

  .centered-text.stay {
    margin-left: 45%;
  }

  .ellipse {
    width: 385px;
    height: 200px;
  }

  .ellipse.header_ellipse {
    width: 465px;
    height: 240px;
  }

  .white-ellipse {
    width: 385px;
    height: 200px;
    bottom: 32%;
    right: 9%;
  }
}
@media (max-width:700px) {
  .slide-content {
    padding: 20px 40px;
  }
  .slide-content .quote{
    margin-left: 20%;
  }
  .dog-image{
    bottom: 10%;
  }
  .title, .centered-text{
    font-size: 25px;
  }
  .navigation-button{
    top:35%;
  }
  .subtitle{
    font-size: 12px;
    white-space: nowrap;
  }
}
@media (max-width:500px){
  .title, .centered-text{
    font-size: 20px;
  }
}
</style>