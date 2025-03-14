<template>
  <div class="col-6">
    <div :class="$style.backgroundWrapper">
      <div :class="$style.backgroundImage"></div>
      <div :class="$style.backgroundImage"></div>
      <div :class="$style.backgroundImage"></div>
      <div :class="$style.backgroundImage"></div>
      <div :class="$style.backgroundImage"></div>
      <div :class="[$style.backgroundImage, $style.text]">
        <div class="h-100 w-100 d-flex align-items-end">
          <h3>
            Revolutionizing <br />
            Drug Discovery & Toxicology Studies
          </h3>
        </div>
      </div>
      <div :class="$style.backgroundImage"></div>
      <div :class="$style.backgroundImage"></div>

      <div :class="$style.backgroundImage"></div>
      <div :class="$style.backgroundImage"></div>
      <div :class="[$style.backgroundImage, $style.text]">
        <div class="h-100 w-100 d-flex align-items-end">
          <span>
            Innovative Technology<br />
            Accuracy and Speed <br />Customized Solutions <br />Expert Support
          </span>
        </div>
      </div>
      <div :class="$style.backgroundImage"></div>
      <div :class="$style.backgroundImage"></div>
      <div :class="$style.backgroundImage"></div>
      <div :class="$style.backgroundImage"></div>
      <div :class="$style.backgroundImage"></div>
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
</style>
