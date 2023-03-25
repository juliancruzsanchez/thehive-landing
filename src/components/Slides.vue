<template>
  <div class="slides" slide="1">
    <div :class="`slide ${$props.current == 1 ? 'current' : ''}`">
      <img class="ios" src="../assets/iphone.png" />
      <img class="android" src="../assets/android.png" />
    </div>
    <div :class="`slide p-5 center-div max-w-[50vh] ${$props.current == 2 ? 'current' : ''}`">
      <div>
        <h1 class="text-3xl font-bold">Our Mission</h1>
        <br>
        <p>
        <ul>
          <li> The Bee is a social media network focused on promoting freedom of expression and individual choice.
          </li><br>
          <li>Users have the ability to choose their own content filters, allowing them to curate their own experience on
            the
            platform.</li><br>
          <li>The platform prioritizes user privacy and security, with robust measures in place to protect user data and
            prevent
            censorship.</li><br>
          <li>The Bee fosters a community of open-minded individuals who value free speech and diverse perspectives.</li>
          <br>
          <li>Users can share a variety of content, including text, images, videos, and links, without fear of being
            censored or
            restricted.</li><br>
        </ul>
        </p>
      </div>

    </div>
    <div :class="`slide center-div ${$props.current == 3 ? 'current' : ''}`">
      <div class="grid gap-5 p-5">
        <h1 class="text-3xl">Thank You for Signing Up!!</h1>
        <button class="button" @click="$emit('donate', 1.00)">Donate $1.00</button>
        <button class="button" @click="$emit('donate', 3.00)">Donate $3.00</button>
        <button class="button" @click="$emit('donate', 5.00)">Donate $5.00</button>
        <div class="subscribe-wrapper">
          <input class="input" v-model="donateAmount" step="0.01" type=" number" placeholder="Donate More" />
          <button @click="$emit('donate', donateAmount)" class="button">Donate</button>
        </div>
      </div>
    </div>
    <div :class="`slide center-div ${$props.current == 4 ? 'current' : ''}`">
      <h1 class="text-3xl">Thank You for Your Donation!!</h1>
    </div>

  </div>
</template>
<script>
export default {
  props: ["current"],
  data() {
    return {
      donateAmount: ""
    }
  }
}
</script>
<style lang="scss">
.slides {
  background: rgba(255, 205, 0, 0.6705882353);
  display: grid;
}

.slide img {
  max-height: 100%;
}

.slide {
  max-height: calc(100vh - 130px - 54px - 24px);
  transition: all 0.5s ease-in-out;
  opacity: 0;
  grid-column: 1;
  grid-row: 1;
}

.slide.current {
  opacity: 1;
  z-index: 1000;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity .5s;
}

.fade-enter,
.fade-leave-to

/* .fade-leave-active below version 2.1.8 */
  {
  opacity: 0;
}
.ios, .android {
  display: inline-block;
}

@supports (-webkit-touch-callout: none) {
  .android {
    display: none !important;
  }
}

@supports not (-webkit-touch-callout: none) {
  .ios {
    display: none !important;
  }
}


</style>