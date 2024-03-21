<template>
  <HeaderComp />
  <div class="container-photo">
    <img class="pointy-photo" src="@/assets/hero.jpg" alt="Hero Image">
    <div class="headline-container">
      <h1>This is headline</h1>
      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Tempus massa est scelerisque penatibus. </p>
    </div>
  </div>
  <div class="container-box">
    <BoxContainer text="Lorem ipsum dolor sit amet, consectetur adipiscing elit." color="#181818" background="#E5EAEE"
      titleSize="29px" />
    <BoxContainer text="Lorem ipsum dolor sit amet, consectetur adipiscing elit." color="#fff" background="#181818"
      titleSize="29x" />
    <BoxContainer
      text="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Tempus massa est scelerisque penatibus."
      color="#181818" background="map" titleSize="36px" />
  </div>

  <TextSection />
  <ActionPage />
  <FooterComp />

</template>

<script>
import HeaderComp from './components/HeaderComp.vue';
import TextSection from './components/TextSection.vue';
import ActionPage from './components/ActionPage.vue';
import FooterComp from './components/FooterComp.vue';
import BoxContainer from './components/BoxContainer.vue';

export default {
  name: 'App',
  components: {
    HeaderComp,
    TextSection,
    FooterComp,
    ActionPage,
    BoxContainer
  }
}
</script>

<style lang="scss">
body,
html {
  margin: 0;
  padding: 0;
  height: 100%;
  font-family: "Inter", sans-serif;
}

.container-photo {
  position: relative;
  height: 100%;

  img {
    background: linear-gradient(180deg, rgba(0, 0, 0, 0.66) 6.22%, rgba(255, 255, 255, 0) 51.23%);
  }
}

.pointy-photo {
  top: 0;
  left: 0;
  width: 100%;
  height: 71vh;
  clip-path: polygon(0 0, 100% 0, 100% 80%, 50% 100%, 0 80%);
  object-fit: cover;
  filter: brightness(0.7);
}

.headline-container {
  display: flex;
  position: absolute;
  display: flex;
  position: absolute;
  top: 15vh;
  left: 5vw;
  flex-direction: column;
  width: 34vw;

  h1 {
    text-transform: uppercase;
    color: #fff;
    font-size: 5.5vw;
    margin: 0;
  }

  p {
    color: #fff;
    font-size: 1.5vw;
  }
}

.container-box {
  display: flex;
  width: 100%;
}

.box {
  flex-grow: 1;
  height: 43vh;
  background-color: #E5EAEE;
  margin-top: -14vh;
  padding: 3vw;
  box-sizing: border-box;

  .date {
    color: #181818;
    padding-top: 14vh;
    font-size: 19px;
    font-weight: 700;
    margin-bottom: 2vw;
  }

  .headline {
    color: #C4132F;
    text-transform: uppercase;
    font-weight: 700;
    font-size: 29px;
    margin-bottom: 0;
  }

  .subtitle {
    color: #181818;
    text-transform: uppercase;
    font-weight: 700;
    font-size: 19px;
    margin-top: 0.3vw;
  }

  .text {
    color: #181818;
    font-weight: 500;
    font-size: 16px;
    width: 80%;
  }
}

.box:nth-child(2) {
  background-color: #181818;

  .date {
    color: #fff;
  }

  .subtitle {
    color: #fff;
  }

  .text {
    color: #fff;
  }
}

.box:nth-child(3) {
  background-image: url('~@/assets/map.svg');
  width: 51%;
  background-repeat: no-repeat;
  background-size: cover;

  .headline {
    font-size: 36px;
  }

  .text {
    width: 42%;
  }
}

@media screen and (max-width: 431px) {
  .container-photo {
    position: absolute;
    top: 0;
  }

  .pointy-photo {
    height: 73vh;
  }

  .headline-container {

    h1 {
      font-size: 9.5vw;
    }

    p {
      font-size: 2.5vw;
    }
  }

  .container-box {
    margin-top: 115vw;
  }

  .box {
    margin-top: -15vh;

    .date {
      font-size: 2vw;
      padding-top: 23vh;
    }

    .headline {
      font-size: 2vw;
    }

    .subtitle {
      font-size: 2vw;
    }

    .text {
      font-size: 1.5vw;
    }
  }

  .box:nth-child(3) {
    width: 91%;

    .headline {
      font-size: 3vw;
    }
  }
}
</style>
