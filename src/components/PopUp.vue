<template>
    <div id="pop-up">
        <div class="square">
            <div class="question">
                <h1> {{ questions[currQues] }} </h1>
                <table>
                    <tr v-for="(ans, index) in answers" :key="index" @click="checkAnswer(index)">
                        <td> {{ ans }} </td>
                    </tr>
                </table>
            </div>
        </div>
        <div v-if="showFeedback" :class="showCorrect ? 'correct' : 'false'">
            <h1 v-if="showCorrect" class="check-text">כל הכבוד! הצלחתם לפוצץ את האסטרואיד!</h1>
            <h1 v-else class="check-text">אוי לא! לא הצלחתם לפוצץ את האסטרואיד!</h1>
        </div>
    </div>
</template>

<script>
    export default {
        name: "pop-up",
        data() {
            return {
                questions: [
                    "מהו אסטרואיד?",
                    "מהו אסטרואיד בייבי?",
                    "מהו אסטרואיד נער מתבגר?",
                    "מהו אסטרואיד בוגר?"
                ],
                answers: [
                    "יצור מרושע שמטרתו להשמיד את כדור הארץ.",
                    "אסטרואיד ממש קטן שהורס רק שכונות מקומיות",
                    "אסטרואיד שבכוונה מנסה להפציץ מקומות שהוא לא אוהב.",
                    "אסטרואיד ממש גדול שיכול להשמיד את כל כדור הארץ."
                ],
                currQues: 0,
                correctAns: [],
                showCorrect: false,
                showFalse: false,
                showFeedback: false,
            }
        },
        methods: {
            showQuestion() {
                let random = Math.round(Math.random() * 3);
                while(this.correctAns.includes(random)) {
                    random = Math.round(Math.random() * 3);
                }
                this.currQues = random;
            },
            checkAnswer(ansNum) {
                if(ansNum === this.currQues) {
                    this.correctAns.push(this.currQues);
                    this.showFalse = false;
                    this.showCorrect = true;
                } else {
                    this.showCorrect = false;
                    this.showFalse = true;
                }
                this.showFeedback = true;
                setTimeout(() => {
                    this.showFeedback = false;
                    this.$emit('hide-pop-up');
                }, 3500);
            },
        }
    }
</script>

<style scoped>
    .square {
        background-image: url("@/assets/light-blue-square.svg");
    }

    .false {
        background-image: url("@/assets/red-square.svg");
        z-index: 5;
    }

    .correct {
        background-image: url("@/assets/green-square.svg");
        z-index: 5;
    }

    .check-text {
        left: 50%;
        transform: translateX(-50%);
        top: 5rem;
        position: absolute;
        width: 11rem;
    }

    .square, .false, .correct {
        width: 15rem;
        height: 15rem;
        background-size: 100% 100%;
        background-repeat: no-repeat;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        position: absolute;
    }

    td {
        border: solid black 0.05rem;
        font-size: 0.7rem;
        padding: 0.2rem;
    }

    h1 {
        font-size: 1rem;
        text-align: center;
    }
    table {
        border-collapse: collapse;
        width: 13rem;
    }

    .question {
        left: 50%;
        transform: translateX(-50%);
        position: absolute;
        top: 1rem;
    }

</style>