<template>
  <div id="asteroid">
    <div :class="[asteroidType]" @click="uncoverText">
      <div class="text" v-if="showText">
        <div v-if="clicked">
          <p> {{ info[0] }} </p>
          <p> {{ info[1] }} </p>
        </div>
        <div v-else>
          <p>מי אני?</p>
          <p>לחצו עליי וגלו!</p>
        </div>
      </div>
    </div>
  </div>
</template>
  
<script>

  export default {
    name: "asteroid",
    props: ["info"],
    data() {
      return {
        clicked: false,
        showText: true,
        asteroidType: 'static',
      }
    },
    methods: {
      uncoverText() {
        console.log("clicked");
        this.clicked = true;
        this.showText = false;
        this.asteroidType = 'explosion';
        setTimeout(() => {
          this.asteroidType = 'none';
          this.showText = true; 
        }, 500);
      },
    },

  }
</script> 
  
<style scoped>
  .static {
    background-image: url("@/assets/asteroid.svg"); 
    z-index: 1;
  }  
  
  .static, .explosion, .none {
    background-size: 100% 100%;
    width:  100%;
    height: 100%;
    background-repeat: no-repeat;
  }
  
    .explosion {
      background-image: url("@/assets/explosion.gif");
      z-index: 5;
    }

  .text {
    text-align: center;
    color: white;
    font-size: 60%;
    line-height: 90%;
    padding: 12%;
    width: 73%;
  }

  .none {
    background-image: none;
  }

  

</style>