<template>
  <div id="game">
    <img class="spaceship" src="@/assets/spaceship-without-fire.svg" alt="spaceship">
    <img class="aim" draggable="true" @drag-start="startDrag" @click="checkEl" src="@/assets/aim.png" alt="aim">
    <div class="lives">
      <img class="star" v-for="index in lives" :key="index" src="@/assets/star.svg" alt="star">
    </div>
    <div class="dimentions">
      <div class="right">
        <p>10</p>
        <p>5</p>
        <p>0</p>
        <p>-5</p>
        <p>-10</p>
      </div>
      <div class="left">
        <p>10</p>
        <p>5</p>
        <p>0</p>
        <p>-5</p>
        <p>-10</p>
      </div>
    </div>
    <div class="wrong-drop" @drop="wrongDrop" @dragover.prevent @dragenter.prevent></div>
    <div class="drop-zone" @drop="onDrop" @dragover.prevent @dragenter.prevent></div>
    <pop-up v-if="showPopUp"></pop-up>
  </div>
</template>
  
<script>
import PopUp from './PopUp.vue';
import VueDragDrop from '@seregpie/vuedragdrop';

  export default {
    name: "game",
    components: {
      [VueDragDrop.DragItem.name]: VueDragDrop.DragItem,
    [VueDragDrop.DropArea.name]: VueDragDrop.DropArea,
      PopUp
    },
    data() {
      return {
        lives: 3,
        showPopUp: false,

      }
    },
    methods: {
      startDrag(evt) {
        console.log("drag");
        evt.dataTransfer.dropEffect = 'move';
        evt.dataTransfer.effectAllowed = 'move';
        evt.dataTransfer.setData("text/plain", "This text may be dragged");
      },
      onDrop() {
        alert('success');
      },
      checkEl() {
        console.log("clicked");
      },
      generateCoordinats() {
        let randomX = Math.round(Math.random() * (10 -(-10)) + 10);
        let randomY = Math.round(Math.random() * (10 -(-10)) + 10);
        return [randomX, randomY];
      },
      wrongDrop() {
        alert('wrong drop');
      }
    },
    // computed: {
    //   listOne() {
    //     return this.items.filter((item) => item.list === 1)
    //   },
    //   listTwo() {
    //     return this.items.filter((item) => item.list === 2)
    //   },
    // },

  }
</script>
  
<style scoped>
  .spaceship {
    position: absolute;
    height: 5rem;
    width: 7rem;
    left: 50%;
    transform: translateX(-50%);
    bottom: 0rem;
  }

  .aim {
    position: absolute;
    height: 1.5rem;
    width: 1.5rem;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    z-index: 5;
  }

  .lives {
    display: flex;
    width: 15rem;
    justify-content: space-evenly;
    flex-direction: row;
    left: 50%;
    transform: translateX(-50%);
    position: absolute;
    top: 2rem;
  }

  .star {
    width: 1rem;
    height: 1rem;
  }

  .dimentions {
    color: white;
    font-size: 0.7rem;
  }

  .right {
    text-align: right;
  }

  .left {
    left: 0rem;
    text-align: left;
  }

  .right, .left {
    display: flex;
    flex-direction: column;
    position: absolute;
    height: 18rem;
    justify-content: space-between;
    top: 50%;
    transform: translateY(-50%);
    direction: ltr;
    margin: 0.5rem;
  }

  .drop-zone {
    width: 2.5rem;
    height: 2.5rem;
    border: dashed white 2px;
    border-radius: 50%;
  }

  .wrong-drop {
    background-color: blue;
    height: 18rem;
    width: 100%;
    position: absolute;
    top: 6rem;
    display: grid;
    grid-template: repeat(20, 1fr) / repeat(10, 1);
  }

</style>