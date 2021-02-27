<template>
  <div class="shorten">
    <div class="shorten-wrapper app-wrap">
      <form class="shorten-form" @submit="submitShortenForm">
        <input
          type="text"
          placeholder="Shorten a link here..."
          v-model="link"
          @input="isFormError = false"
          :class="{ 'form-error': isFormError }"
        />
        <input type="submit" class="button-link" value="Shorten It!" />
        <p class="shorten-error" v-if="isFormError">Please add a link</p>
      </form>
    </div>
  </div>
  <div class="shorten-result">
    <div class="shorten-result-wrapper app-wrap">
      <div
        class="shorten-result-item"
        v-for="(link, index) in shortLinks"
        :key="link"
      >
        <div class="shorten-input-wrapper">
          <p class="shorten-input">{{ link.original }}</p>
          <hr />
          <p class="shorten-output">{{ link.short }}</p>
        </div>
        <button
          class="button-link"
          :class="{ copied: link.copied }"
          @click="copyLink(index)"
        >
          {{ link.copied ? "Copied!" : "Copy" }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Shorten",
  data() {
    return {
      isFormError: false,
      link: null,
      shortLinks: [],
    };
  },
  methods: {
    submitShortenForm(e) {
      if (!this.link) {
        this.isFormError = true;
      } else {
        axios
          .get(`https://api.shrtco.de/v2/shorten?url=${this.link}`)
          .then((result) => {
            const item = {
              original: result.data.result.original_link,
              short: result.data.result.short_link,
              copied: false,
            };

            const newLinks = [item, ...this.shortLinks];
            console.log(newLinks);
            if (newLinks.length >= 4) {
              newLinks.pop();
            }
            this.shortLinks = newLinks;
          })
          .catch((err) => {
            if (err.response.data.error_code === 2) this.isFormError = true;
          });
      }

      e.preventDefault();
    },
    copyLink(linkIndex) {
      let i;
      for (i = 0; i < this.shortLinks.length; i += 1) {
        this.shortLinks[i].copied = false;
      }
      this.shortLinks[linkIndex].copied = true;
    },
  },
};
</script>

<style scoped lang="scss">
@import "./utility/utility";

.shorten {
  background: linear-gradient($primary-0 50%, $neutral-4 50%);
}

.shorten-form {
  background-image: url("../assets/bg-shorten-desktop.svg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  background-color: $primary-2;
  border-radius: $s-12;

  padding: $s-48;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;

  @include for-size(b2) {
    padding: $s-40 $s-32;
  }

  @include for-size(b3) {
    flex-direction: column;
    flex-wrap: nowrap;
  }

  @include for-size(b4) {
    padding: $s-24;
    flex-wrap: nowrap;
  }

  @include for-size(mobile) {
    background-image: url("../assets/bg-shorten-mobile.svg");
  }
}

input[type="text"] {
  padding: $s-14 $s-30;
  display: inline-block;
  border: 2px solid $neutral-2;
  border-radius: $s-12;
  box-sizing: border-box;
  outline: none;

  font-family: inherit;
  font-size: $s-16;

  flex-grow: 2;
  margin-right: $s-40;

  &.form-error {
    border-color: $secondary-0;
  }

  @include for-size(b2) {
    margin-right: $s-20;
  }
  @include for-size(b3) {
    margin-right: 0;
  }
  @include for-size(mobile) {
    padding: $s-14 $s-20;
  }
}

input[type="submit"] {
  border: none;
  cursor: pointer;
  border-radius: $s-12;
  padding: $s-16 $s-40;
  font-size: $s-16;

  @include for-size(b3) {
    margin-top: $s-16;
    order: 2;
  }
}

.shorten-error {
  color: $secondary-0;
  font-style: italic;
  font-size: $s-14;
  margin: 0;
  flex-basis: 100%;
  height: 0;
}

/******** RESULTS ********/

.shorten-result {
  background-color: $neutral-4;
}

.shorten-result-item {
  background-color: $primary-0;
  padding: $s-20;
  border-radius: $s-8;
  margin-top: $s-20;

  display: flex;

  @include for-size(b3) {
    flex-direction: column;
    padding: $s-20 0;
  }

  .shorten-input-wrapper {
    display: flex;
    justify-content: space-between;
    align-content: center;
    flex-grow: 2;
    padding: 0 $s-30;

    p {
      display: inline-block;
      align-self: center;
      margin: 0;
    }

    .shorten-input {
      width: 600px;
      overflow: hidden;
      text-overflow: ellipsis;

      @include for-size(b1) {
        width: 500px;
      }

      @include for-size(b2) {
        width: 330px;
      }

      @include for-size(b3) {
        width: 100%;
      }
    }

    .shorten-output {
      color: $primary-1;
    }

    hr {
      display: none;
    }

    @include for-size(b3) {
      flex-direction: column;
      padding: 0;

      p {
        width: 100%;
        box-sizing: border-box;
        padding: 0 $s-20 $s-8 $s-20;
      }

      hr {
        display: unset;
        margin: 0;
        margin-bottom: $s-8;
        border: none;
        height: 1px;
        background-color: $neutral-5;
      }
    }
  }

  button {
    padding: $s-8 $s-30;
    display: inline-block;
    border: none;
    border-radius: $s-8;
    box-sizing: border-box;
    outline: none;
    font-family: inherit;
    font-size: $s-14;
    cursor: pointer;
    min-width: 6.25rem;

    &.copied {
      background-color: $primary-2;
      padding: $s-8 $s-20;
    }

    @include for-size(b3) {
      margin: 0 $s-20;
    }
  }
}
</style>
