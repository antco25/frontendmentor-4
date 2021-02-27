<template>
  <div class="header">
    <div class="header-wrapper app-wrap">
      <div class="header-logo">
        <img src="../assets/logo.svg" />
      </div>
      <div
        class="header-mobile-nav"
        @click="isMobileNavOpen = !isMobileNavOpen"
      >
        <img src="../assets/icon-hamburger.svg" />
      </div>
      <nav class="header-nav" :class="{ 'header-nav-active': isMobileNavOpen }">
        <ul class="nav-links">
          <li><a href="#">Features</a></li>
          <li><a href="#">Pricing</a></li>
          <li><a href="#">Resources</a></li>
        </ul>
        <hr class="nav-divider" />
        <ul class="nav-login">
          <li><a href="#">Login</a></li>
          <li class="button-li"><a class="button-link" href="#">Sign Up</a></li>
        </ul>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      isMobileNavOpen: false,
    };
  },
  created() {
    window.addEventListener("resize", this.onWindowResize);
  },
  unmounted() {
    window.removeEventListener("resize", this.onWindowResize);
  },
  methods: {
    onWindowResize(e) {
      if (e.target.outerWidth > 768) {
        this.isMobileNavOpen = false;
      }
    },
  },
};
</script>

<style scoped lang="scss">
@import "./utility/utility";

$link-padding: 30px;
$vertical-padding: 40px;

.header-wrapper {
  display: flex;
  justify-content: space-between;
  padding-top: $vertical-padding;
  padding-bottom: $vertical-padding;

  .header-logo {
    display: inline-block;
    align-self: flex-end;
    padding-top: 14px;
  }

  .header-mobile-nav {
    display: none;
    align-self: center;
    cursor: pointer;
    padding-top: 14px;
  }

  .header-nav {
    display: flex;
    flex-grow: 2;
    justify-content: space-between;

    .nav-links,
    .nav-login {
      align-self: center;
    }
  }

  @include for-size(b3) {
    flex-wrap: wrap;
    .header-logo {
      padding-bottom: 20px;
    }

    .header-mobile-nav {
      display: inline-block;
      padding-bottom: 20px;
    }
    .header-nav {
      flex-basis: 100%;
      flex-direction: column;
      background-color: $primary-2;
      border-radius: $s-14;
      padding: 0;
      max-height: 0;
      opacity: 0;
      overflow-y: hidden;
      transition: 500ms;

      .nav-login {
        width: 100%;
      }

      &.header-nav-active {
        padding: $s-20;
        opacity: 1;
        max-height: 500px;
        overflow-y: unset;
      }
    }
  }
}

.header-nav {
  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }

  li {
    display: inline-block;
    padding-left: $link-padding;
  }

  a {
    color: $neutral-1;
    text-decoration: none;
    outline: none;
    font-size: $s-16;

    &:hover {
      color: $neutral-2;
    }
  }

  .nav-divider {
    display: none;
  }

  .button-link {
    background-color: $primary-1;
    outline: none;
    color: $primary-0;
    font-weight: 700;
    padding: 8px 26px;
    border-radius: 34px;
    text-decoration: none;
    display: inline-block;
    font-size: $s-16;

    &:hover {
      opacity: 0.8;
      color: $primary-0;
    }
  }

  @include for-size(b3) {
    .nav-divider {
      display: unset;
      width: 100%;
      border: none;
      height: 1px;
      background-color: $neutral-5;
    }

    li {
      display: block;
      padding: 10px 0;
      text-align: center;
    }

    a {
      color: $primary-0;
      font-size: $s-16;

      &:hover {
        color: $primary-1;
      }
    }

    .button-link {
      padding-left: 0;
      padding-right: 0;
      width: 100%;
      font-size: $s-16;

      &:hover {
        opacity: 1;
        background-color: $primary-1-active;
      }
    }
  }
}
</style>
