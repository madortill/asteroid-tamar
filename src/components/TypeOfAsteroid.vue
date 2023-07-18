<template>
  <div id="type-of-asteroid">
    <div class="container">
      <Asteroid class="asteroid" v-for="(asteroid, index) in asteroidData" :key="index" :info="asteroid" :id="getObjectKey(asteroidData, asteroid)"></Asteroid>
    </div>
  </div>
</template>
    
<script>
  import Asteroid from './Asteroid.vue';

  export default {
    name: "type-of-asteroid",
    components: {
      Asteroid
    },
    data() {
      return {
        asteroidData: {
          teenager: ['אני אסטרואיד נער מתבגר!', 'אני אסטרואיד שהוא די חרא כי אני בכוונה מנסה להפציץ מקומות שאני לא אוהב.'],
          baby: ['אני אסטרואיד בייבי!', 'אני אסטרואיד ממש קטן והורס רק שכונות מקומיות.'],
          adult: ['אני אסטרואיד בוגר', 'אני אסטרואיד ממש גדול שיכול להשמיד את כל כדור הארץ.']
        }

      }
    },
    methods: {
      getObjectKey(obj, value) {
        return Object.keys(obj).find(key => obj[key] === value);
      }
    },
    computed: {
      
    },
  }
</script>
  
<style scoped>

  .container {
    display: flex;
    flex-direction: column;
    height: 20rem;
    position: relative;
    top: 3rem;
    left: 1rem;
  }
  .asteroid {
    margin: 1rem;
    display: flex;
    position: relative;
  }

  #baby {
    width: 5rem;
    height: 5rem;
    align-self: flex-end;
    top: -2rem;
    left: -1rem;
    position: relative;
    font-size: 0.7rem;
  }

  #teenager {
    width: 11rem;
    height: 11rem;
    font-size: 0.9rem;
  }

  #adult {
    width: 15rem;
    height: 15rem;
    left: 1rem;
    bottom: 3rem;
  }

</style>