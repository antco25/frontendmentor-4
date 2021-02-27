<template>
  <div class="stats">
    <div class="stats-wrapper app-wrap">
      <section class="stats-header">
        <h1>Advanced Statistics</h1>
        <p>
          Track how your links are performing across the web with our advanced
          statistics dashboard.
        </p>
      </section>
      <section class="stats-cards">
        <StatCard
          title="Brand Recognition"
          text="Boost your brand recognition with each click. Generic links don't mean a thing.
          Branded links help instil confidence in your content."
        />
        <StatCard
          title="Detailed Records"
          text="Gain insights into who is clicking your links. Knowing when and where people
          engage with your content helps inform better decisions."
        />
        <StatCard
          title="Fully Customizable"
          text="Improve brand awareness and content discoverability through customizable links,
          supercharging audience engagement."
        />
      </section>
    </div>
  </div>
</template>

<script>
import StatCard from "./StatCard.vue";

export default {
  name: "Statistics",
  components: {
    StatCard,
  },
};
</script>

<style scoped lang="scss">
@import "./utility/utility";

$card-offset: $circle-dia / 2;
$vertical-padding: $s-40;
$bg-line-size: $s-8;

.stats {
  background-color: $neutral-4;

  .stats-wrapper {
    padding-top: $vertical-padding;
    padding-bottom: $vertical-padding;
  }
}

.stats-header {
  text-align: center;
  padding-top: $vertical-padding;
  h1 {
    margin: 0;
    font-size: $s-40;
  }
  p {
    font-size: $s-18;
    color: $neutral-1;
    padding-top: $s-16;
    padding-bottom: $s-30;
    max-width: 47%;
    margin: 0 auto;
  }

  @include for-size(b2) {
    h1 {
      font-size: $s-36;
    }
    p {
      font-size: $s-16;
      max-width: 60%;
    }
  }

  @include for-size(b4) {
    h1 {
      font-size: $s-28;
    }
    p {
      font-size: $s-18;
      max-width: 100%;
    }
  }
}

.stats-cards {
  display: flex;
  margin-left: -$stat-box-margin;
  margin-right: -$stat-box-margin;
  padding: $circle-dia 0;

  background: linear-gradient($primary-1, $primary-1) no-repeat;
  background-size: calc(100% - 2rem) $bg-line-size;
  background-position: center;

  > * {
    flex-basis: 33.33%;
    align-self: center;
  }

  > :first-child {
    position: relative;
    top: -$card-offset;
  }

  > :last-child {
    position: relative;
    top: $card-offset;
  }

  @include for-size(b2) {
    margin-left: -$stat-box-margin-b2;
    margin-right: -$stat-box-margin-b2;
  }

  @include for-size(b3) {
    background-size: $bg-line-size 80%;
    flex-direction: column;
    p {
      max-width: 100%;
    }
  }
}
</style>
