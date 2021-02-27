<template>
  <div class="boost-cta">
    <h1>Boost your links today</h1>
    <a class="button-link" href="#">Get Started</a>
  </div>
  <div class="footer">
    <div class="footer-wrap app-wrap">
      <div class="footer-logo">
        <Logo />
      </div>
      <nav class="footer-features footer-links">
        <h2>Features</h2>
        <ul>
          <li><a href="#">Link Shortening</a></li>
          <li><a href="#">Branded Links</a></li>
          <li><a href="#">Analytics</a></li>
        </ul>
      </nav>
      <nav class="footer-resources footer-links">
        <h2>Resources</h2>
        <ul>
          <li><a href="#">Blog</a></li>
          <li><a href="#">Developers</a></li>
          <li><a href="#">Support</a></li>
        </ul>
      </nav>
      <nav class="footer-company footer-links">
        <h2>Company</h2>
        <ul>
          <li><a href="#">About</a></li>
          <li><a href="#">Our Team</a></li>
          <li><a href="#">Careers</a></li>
          <li><a href="#">Contact</a></li>
        </ul>
      </nav>
      <nav class="footer-media">
        <ul>
          <li>
            <a href="#"
              ><FontAwesomeIcon :icon="['fab', 'facebook-square']" :size="'lg'"
            /></a>
          </li>
          <li>
            <a href="#"
              ><FontAwesomeIcon :icon="['fab', 'twitter']" :size="'lg'"
            /></a>
          </li>
          <li>
            <a href="#"
              ><FontAwesomeIcon :icon="['fab', 'pinterest']" :size="'lg'"
            /></a>
          </li>
          <li>
            <a href="#"
              ><FontAwesomeIcon :icon="['fab', 'instagram']" :size="'lg'"
            /></a>
          </li>
        </ul>
      </nav>
    </div>
  </div>
</template>

<script>
import { library } from "@fortawesome/fontawesome-svg-core";
import {
  faFacebookSquare,
  faTwitter,
  faPinterest,
  faInstagram,
} from "@fortawesome/free-brands-svg-icons";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import Logo from "./utility/Logo.vue";

library.add(faFacebookSquare);
library.add(faTwitter);
library.add(faPinterest);
library.add(faInstagram);

export default {
  name: "Footer",
  components: {
    FontAwesomeIcon,
    Logo,
  },
};
</script>

<style scoped lang="scss">
@import "./utility/utility";

.boost-cta {
  text-align: center;
  padding: 50px 0;
  background-color: $primary-2;
  background-image: url("../assets/bg-boost-desktop.svg");
  background-repeat: no-repeat;
  background-size: cover;

  h1 {
    margin: 0;
    padding-bottom: $s-16;
    color: $primary-0;
    font-size: $s-40;
  }

  @include for-size(b2) {
    h1 {
      font-size: $s-36;
    }
  }

  @include for-size(b4) {
    h1 {
      font-size: $s-28;
    }
  }

  @include for-size(mobile) {
    background-image: url("../assets/bg-boost-mobile.svg");
  }
}

.footer {
  flex-grow: 2;
  background-color: $neutral-2;
  color: $primary-0;

  .footer-wrap {
    display: flex;
    justify-content: space-between;
    align-content: baseline;

    padding-top: 50px;
    padding-bottom: 60px;

    @include for-size(b3) {
      flex-direction: column;
      text-align: center;

      > * {
        padding-bottom: $s-20;
      }
    }
  }
}

.footer-logo {
  display: inline-block;
  flex-basis: 25%;
  .logo {
    fill: $primary-0;
  }

  @include for-size(b2) {
    flex-basis: 0;
  }
}

.footer-links {
  display: inline-block;
  h2 {
    margin: 0;
    font-size: $s-18;
    padding-bottom: $s-16;
  }

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }

  a {
    color: $neutral-0;
    text-decoration: none;
    outline: none;
    font-size: $s-16;

    &:hover {
      color: $primary-1;
    }
  }
}

.footer-media {
  display: inline-block;
  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }

  li {
    display: inline-block;
    padding: 10px;
  }

  a {
    text-decoration: none;
    outline: 0;
    color: white;

    &:hover {
      color: $primary-1;
    }

    svg {
      display: block;
    }
  }
}
</style>
