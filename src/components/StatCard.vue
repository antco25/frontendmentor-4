<template>
  <div class="statCard">
    <div class="img-wrapper circle">
      <img src="../assets/icon-brand-recognition.svg" />
    </div>
    <h1>{{ title }}</h1>
    <p>{{ text }}</p>
  </div>
</template>

<script>
export default {
  name: "StatCard",
  props: ["title", "text"],
};
</script>

<style scoped lang="scss">
@import "./utility/utility";

//Properties

$min-box-dimension: 12.5rem; //200px
$box-margin: $stat-box-margin;
$box-margin-b2: $stat-box-margin-b2;
$box-padding: $s-20;
$box-padding-b2: $s-10;

$header-font-size: $s-24;
$text-font-size: $s-16;
$text-font-size-b2: $s-14;

$circle-rad: $circle-dia / 2;
$text-offset: $circle-rad / 2;

.statCard {
  background-color: white;
  display: inline-block;
  min-width: $min-box-dimension;
  min-height: $min-box-dimension;
  margin: $box-margin;
  padding: $box-padding;
  padding-top: 0;

  h1 {
    margin: 0;
    padding: 0;
    font-size: $header-font-size;
  }
  p {
    margin: 0;
    padding: 0;
    padding-top: $box-padding;
    font-size: $text-font-size;
    color: $neutral-1;
  }

  h1,
  p {
    position: relative;
    bottom: $text-offset;
  }

  .img-wrapper {
    position: relative;
    bottom: $circle-rad;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  @include for-size(b2) {
    margin: $box-margin-b2;
    padding: $box-padding-b2;
    padding-top: 0;

    p {
      font-size: $text-font-size-b2;
    }
  }

  @include for-size(b3) {
    padding: $box-padding;
    text-align: center;

    p {
      font-size: $text-font-size;
    }

    .img-wrapper {
      left: calc(50% - 2.5rem);
    }
  }
}

.circle {
  height: $circle-dia;
  width: $circle-dia;
  background-color: $primary-2;
  border-radius: 50%;
  display: inline-block;
}
</style>
