<template>
  <div class="intro">
    <div class="intro-wrapper app-wrap">
      <section class="intro-header">
        <h1>More than just shorter links</h1>
        <p>
          Build your brand's recognition and get detailed<br />
          insights on how your links are performing
        </p>
        <a class="button-link" href="#">Get Started</a>
      </section>
      <section class="intro-image">
        <img src="../assets/illustration-working.svg" />
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: "Introduction",
};
</script>

<style scoped lang="scss">
@import "./utility/utility";

.intro {
  overflow-x: hidden;
}

.intro-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  padding-bottom: $s-50;

  .intro-header {
    flex-basis: 55%;
  }

  .intro-image {
    min-width: 0;
    flex-basis: 45%;
    position: relative;

    img {
      height: 100%;
      display: block;
    }
  }

  @include for-size(b2) {
    .intro-image {
      height: 24rem;
    }
  }

  @include for-size(b3) {
    .intro-image {
      height: 20rem;
    }
  }

  @include for-size(b4) {
    flex-direction: column;
    height: 40rem; //640px

    .intro-header {
      padding-top: 2rem;
      padding-bottom: 2rem;
      order: 1;
      flex-basis: auto;
    }

    .intro-image {
      width: 100%;
      flex-grow: 1;
      flex-basis: auto;
      img {
        height: 100%;
      }
    }
  }
}

.intro-header {
  h1 {
    margin: 0;
    font-size: 4.25rem; //68px
    line-height: 1.2;
  }
  p {
    margin: 0;
    font-size: $s-18;
    color: $neutral-1;
    padding-top: $s-16;
    padding-bottom: $s-30;
    padding-right: $s-24;
  }

  @include for-size(b2) {
    h1 {
      font-size: $s-48;
    }

    p {
      font-size: $s-16;
    }

    br {
      display: none;
    }
  }

  @include for-size(b3) {
    h1 {
      font-size: $s-36;
    }
  }

  @include for-size(b4) {
    text-align: center;
    h1 {
      font-size: $s-30;
    }

    p {
      font-size: $s-18;
      padding-right: 0;
    }
  }
}
</style>
