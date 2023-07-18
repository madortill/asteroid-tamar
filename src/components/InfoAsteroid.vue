<template>
    <div id="info-asteroid">
        <div class="scene scene--card">
        <div :class="isFlip === true ? 'card is-flipped' : 'card'">
            <div @click="flip" class="card__face card__face--front">
                <span class="text">
                    <div class="line">מהו אסטרואיד?</div>
                    <div class="line">לחץ עליי וגלה</div>
                </span>
            </div>
            <div @click="flip" class="card__face card__face--back">
                <div class="back-text">אסטרואיד הוא יצור מרושע שמטרתו להשמיד את כדור הארץ ואנחנו בברוגז איתו ממש. הוא נראה כמו כדור עגול כזה אבל לא חלק כי יש לו בליטות מכוערות שנראות כמו חצ'קונים.</div>
            </div>
        </div>
        </div>
    </div>
</template>
    
<script>
  
    export default {
        name: "info-asteroid",
        data() {
            return {
                isFlip: false,
                cntFlip: 0
            }
        },
        methods: {
            flip() {
                this.cntFlip += 1;
                this.isFlip = true;
                if (this.cntFlip % 2 === 0) {
                    this.isFlip = false;
                }
            }
        }
    }
 </script>
    
<style scoped>

    h1 {
        text-align: center;
        color: white;
    }
    .scene {
        display: inline-block;
        margin: 1rem 0;
        perspective: 600px;
    }

    .card {
        position: relative;
        top: 2rem;
        width: 100%;
        height: 100%;
        cursor: pointer;
        transform-style: preserve-3d;
        transform-origin: center right;
        transition: transform 1s;
    }

    .card.is-flipped {
        transform: translateX(-15rem) rotateY(-180deg);
    }

    .card__face {
        margin-top: 15vh;
        display: flex;
        position: absolute;
        width: 13rem;
        height: 13rem;
        line-height: 2rem;
        color: white;
        text-align: center;
        font-weight: bold;
        font-size: 1rem;
        backface-visibility: hidden;
        flex-wrap: wrap;
        flex-direction: column;
        align-content: center;
    }

    .card__face--front {
        right: 2rem;
        left: 2rem;
    }

    .card__face--front, .card__face--back {
        background-image: url("@/assets/asteroid.svg");
        background-repeat: no-repeat;
        position: absolute;
    }

    .card__face--back {
        transform: rotateY(180deg);
    } 
    
    .text {
        display: flex;
        width: 65%;
        height: 20%;
        text-align: center;
        color: white;
        font-size: 1rem;
        font-weight: 500;
        justify-content: center;
        flex-wrap: nowrap;
        flex-direction: column;
        align-items: center;
        margin-top: 4.5rem;
    }

    .line {
        height: 1.7rem;
    }

    .back-text {
        width: 10rem;
        height: 10rem;
        line-height: normal;
        text-align: center;
        color: white;
        font-size: 0.7rem;
        font-weight: 500;
        padding: 3.5rem;
    }
</style>