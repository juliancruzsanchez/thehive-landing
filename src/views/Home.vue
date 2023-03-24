<template>
  <div class="page">
    <div class="topbar" @click="currentSlide = 1"></div>
    <!-- Desktop-->
    <div class="desktop-phone center-div" style="transform: translateY(-150px) scale(95%);">
      <div class="grid gap-5 slide-container">
        <Slides :current="currentSlide" @donate="amt => donate(amt)"></Slides>
        <div>
          <div class="subscribe-wrapper" v-if="currentSlide == 1 || currentSlide == 2">
            <input class="input" type="text" placeholder="Enter email address" autocomplete="off" v-model="email"
              @click="() => { currentSlide = 2; document.body.scrollTop = document.documentElement.scrollTop = 0; }" />
            <button class="button" @click="getNotified()">Get Notified</button>
          </div>
          <span v-if="currentSlide == 1 || currentSlide == 2">By pressing get notified you agree to our
            <a class="font-bold" href="/#/legal">Terms and Agreements</a>
          </span>
        </div>

      </div>
    </div>
    <div class="sidetext-wrapper">
      <div class="sidetext">
        Your Hive.<br>
        Your Choice.<br>
        Your Way.<br>
      </div>
    </div>

    <!-- Mobile -->

    <div class="center-div mobile-steps">
      <Slides :current="currentSlide" @donate="amt => donate(amt)"></Slides>
    </div>
    <div class="grid center-div mobile-signup-wrapper mt-5 mx-5" v-if="currentSlide == 1 || currentSlide == 2">
      <input class="input" type="text" placeholder="Enter email address" autocomplete="off" v-model="email"
        @focus="currentSlide = 2" />
      <button class="button" @click="getNotified()">Get Notified</button>
    </div>

    <span class="center-div" style="font-size: 12px" v-if="currentSlide == 1 || currentSlide == 2">By pressing get
      notified you agree to our
      &nbsp;
      <a class="font-bold" href="/#/legal">Terms and Agreements</a>
    </span>

  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Slides from '../components/Slides.vue';

export default {
  name: 'Home',
  components: {
    HelloWorld,
    Slides
  },
  data() {
    return {
      currentSlide: 1,
      email: ""
    }
  },
  methods: {
    getNotified() {
      var validRegex = /^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/;
      if (this.$data.email !== "" && this.$data.email.match(validRegex)) {
        this.$data.currentSlide = 3
      } else {
        alert("Invalid Email! Please try again.")
        this.$data.email = ""
      }
    },
    donate(amt) {
      console.log(amt)
      this.$data.currentSlide = 4
    }
  }
}
</script>

<style lang="scss">
html {
  background-image: url(../assets/hive.png);
  background-position: top right;
  background-repeat: no-repeat;
  background-color: #FFCD00;
}

.topbar {
  background: url(../assets/logo.png), #ffcd00ab;
  background-position: center center;
  background-repeat: no-repeat;
  background-size: contain;
  height: 100px;
  padding: 15px;

}

.subscribe-wrapper {
  display: grid;
  grid-template-columns: 1fr auto;
  grid-gap: 10px;
  font-size: 24px;
}

.input {
  background-color: #FFE98E;
  padding: 15px;
  width: 100%;
  border-radius: 8px;
  box-shadow: 0px 2px 4px #00000023;
}

.button {
  color: #FFCD00;
  background: #000;
  border-radius: 8px;
  padding: 15px;
}

.sidetext-wrapper {
  display: none;
  position: fixed;
  top: 50%;
  transform: translate(20px, -50%);
  font-size: 24px;
}

.sidetext {
  font-size: 70px;
  font-weight: bold;
  margin-bottom: 20px;
}

.desktop-phone {
  display: none;
}

.phone-mobile {
  height: 75vh;
  margin-top: 0.625rem;
  padding-left: 10px;
  padding-right: 10px;
}

.motto {
  font-size: 40px;
  font-weight: bold;
  margin-bottom: 20px;
  margin-top: 20px;
  text-align: center;
}

.mobile-signup-wrapper {
  display: grid;
  grid-template-columns: 1fr auto;
  grid-gap: 10px;
}

.slide-container {
  height: 100vh;
  grid-template-rows: 1fr auto;
}

@media (min-width: 1262px) {

  html,
  body {
    height: 100vh;
    overflow: hidden;
  }

  .topbar {
    background-image: url(../assets/logo-cs.png);
    background-color: #00000000;
    background-position: top left;
    margin: 10px;
    height: 150px;
  }

  .sidetext-wrapper {
    display: block;
  }

  .desktop-phone {
    display: flex;
  }

  .phone-mobile {
    display: none;
  }

  .mobile-signup-wrapper {
    display: none !important;
  }

  .slide {
    height: auto
  }

  .mobile-steps {
    display: none;
  }
}

.keyboardOpen {
  color: red;
}
</style>
