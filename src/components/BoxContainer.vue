<template>
  <div class="box" :class="{ 'has-map': background === 'map' }" :style="{ background: background }">
    <p class="date" :style="{ color: color }">17 MAI</p>
    <h2 class="headline" :class="{ 'normal-size': titleSize === '29px', 'large-size': titleSize === '36px' }">Headline
      Beitrag 2021</h2>
    <h3 class="subtitle" :style="{ color: color }">Subtitle</h3>
    <p class="text" :style="{ color: color }">{{ text }}</p>
  </div>
</template>

<script>
export default {
  name: 'BoxContainer',
  props: [
    "color",
    "titleSize",
    "background",
    "text"
  ]
}
</script>

<style lang="scss">
.normal-size {
  font-size: 29px;
}

.large-size {
  font-size: 36px;
}

.has-map {
  background-image: url('../assets/map.svg');
  width: 51%;
  background-repeat: no-repeat;
  background-size: cover;
}

.box {
  flex-grow: 1;
  height: 43vh;
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

@media screen and (max-width: 431px) {
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



  .has-map {
    width: 91%;

    .headline {
      font-size: 3vw;
    }
  }
}
</style>
