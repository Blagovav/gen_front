<template>
  <div class="col-6">
    <div :class="$style.backgroundWrapper">
      <div :class="[$style.backgroundImage, $style.img1]"></div>
      <div :class="[$style.backgroundImage, $style.img2]"></div>
      <div :class="[$style.backgroundImage, $style.img3]"></div>
      <div :class="[$style.backgroundImage, $style.img4]"></div>
      <div :class="[$style.backgroundImage, $style.img5]"></div>
      <div :class="[$style.backgroundImage, $style.text, $style.img6]">
        <div class="h-100 w-100 d-flex align-items-end">
          <h3>
            Revolutionizing <br />
            Drug Discovery & Toxicology Studies
          </h3>
        </div>
      </div>
      <div :class="[$style.backgroundImage, $style.img7]"></div>
      <div :class="[$style.backgroundImage, $style.img8]"></div>

      <div :class="[$style.backgroundImage, $style.img9]"></div>
      <div :class="[$style.backgroundImage, $style.img10]"></div>
      <div :class="[$style.backgroundImage, $style.text, $style.img11]">
        <div class="h-100 w-100 d-flex align-items-end">
          <span>
            Innovative Technology<br />
            Accuracy and Speed <br />Customized Solutions <br />Expert Support
          </span>
        </div>
      </div>
      <div :class="[$style.backgroundImage, $style.img12]"></div>
      <div :class="[$style.backgroundImage, $style.img13]"></div>
      <div :class="[$style.backgroundImage, $style.img14]"></div>
      <div :class="[$style.backgroundImage, $style.img15]"></div>
      <div :class="[$style.backgroundImage, $style.img16]"></div>
    </div>
  </div>
</template>

<style module>
.backgroundWrapper {
  display: grid;
  border-radius: 45px;
  grid-template-rows: auto 320px 320px auto;
  grid-template-columns: auto 296px 296px auto;
  width: 100%;
  height: 100%;
  gap: 10px;
}

.backgroundImage {
  border-radius: 45px;
  background-image: url('../assets/login_background.png');
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
}

.backgroundImage.text {
  background-image: none;
  background-color: white;
  padding: 15px;
}

.text h3 {
  color: rgba(15, 23, 42, 1);

  font-weight: 600;
  font-size: 24px;
  line-height: 129%;
  letter-spacing: 0%;
}

.text span {
  margin-left: 10px;
  margin-bottom: 10px;
  color: rgba(15, 23, 42, 1);

  font-weight: 600;
  font-size: 16px;
  line-height: 129%;
  letter-spacing: 0%;
}

.img1 {
  background-image: url('../assets/background/1.png');
}
.img2 {
  background-image: url('../assets/background/2.png');
}
.img3 {
  background-image: url('../assets/background/3.png');
}
.img4 {
  background-image: url('../assets/background/4.png');
}
.img5 {
  background-image: url('../assets/background/5.png');
}
.img6 {
  background-image: url('../assets/background/6.png');
}
.img7 {
  background-image: url('../assets/background/7.png');
}
.img8 {
  background-image: url('../assets/background/8.png');
}

.img9 {
  background-image: url('../assets/background/9.png');
}
.img10 {
  background-image: url('../assets/background/10.png');
}
.img11 {
  background-image: url('../assets/background/11.png');
}
.img12 {
  background-image: url('../assets/background/12.png');
}
.img13 {
  background-image: url('../assets/background/13.png');
}
.img14 {
  background-image: url('../assets/background/14.png');
}
.img15 {
  background-image: url('../assets/background/15.png');
}
.img16 {
  background-image: url('../assets/background/16.png');
}
</style>
