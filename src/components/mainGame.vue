<script >
let interval;
import { spellsData } from './spellsData.js';
export default {
    data() {
        return {
            seconds: 0,
            millieseconds: 0,
            b: 0,
            colbs: ['', '', ''],
            spellUrl: "",
            spellName: "",
            spellIndex: 0,
            userRecord: 0,
            newRecord: true,
            userRank: "",
            isGameStarted: false,
            colb1: "",
            colb2: "",
            colb3: "",
            spells: [...spellsData]

        }
    },
    methods: {
        startTimer() {
            this.millieseconds++

            if (this.millieseconds >= 99) {
                this.seconds++
                this.millieseconds = 0
            }
        },

        startStopWatch() {
            interval = setInterval(this.startTimer, 10)
        },
        stopStopWatch() {
            clearInterval(interval)
        },
        resetStopWatch() {
            clearInterval(interval)
            this.seconds = 0
            this.millieseconds = 0
        },
        chooseSpell() {
            if (this.spells.length === 0) {                
                this.spells = [...spellsData]
                let userTime = this.seconds + this.millieseconds / 100
                this.b = 2
                this.stopStopWatch()
                if (this.userRecord === 0 || this.userRecord > userTime) {
                    this.userRecord = userTime
                } else {
                    this.newRecord = false
                }
                if (userTime >= 25) { this.userRank = "src/assets/ranks/herald.png" }
                if (userTime < 25 && userTime >= 20) { this.userRank = "src/assets/ranks/guardian.webp" }
                if (userTime < 20 && userTime >= 15) { this.userRank = "src/assets/ranks/crusader.webp" }
                if (userTime < 15 && userTime >= 10) { this.userRank = "src/assets/ranks/archon.webp" }
                if (userTime < 10 && userTime >= 9) { this.userRank = "src/assets/ranks/legend.webp" }
                if (userTime < 9 && userTime >= 8) { this.userRank = "src/assets/ranks/ancient.webp" }
                if (userTime < 8 && userTime >= 7) { this.userRank = "src/assets/ranks/devine.webp" }
                if (userTime < 7) { this.userRank = "src/assets/ranks/immortal.webp" }
            } 
            else {
                const index = Math.floor(Math.random() * (this.spells.length - 1));

                this.spellIndex = index
                this.spellUrl = this.spells[index].imgUrl
                this.spellName = this.spells[index].name
            }


        },
        startGame() {
            this.b = 1
            this.isGameStarted = true
            this.startStopWatch()
            this.chooseSpell()
            console.log(this.spells);
        },
        registrateClick(pressedKey) {
            if (this.isGameStarted) {
                if (pressedKey === 82 && this.colbs[2] != '') {
                    console.log("before cheking combination");
                    this.checkCombination()
                }
                else {
                    this.colbs[2] = this.colbs[1]
                    this.colbs[1] = this.colbs[0]
                    this.colbs[0] = pressedKey
                    console.log(this.colbs);
                    this.changeImageInColbs()
                }
            }
        },
        checkCombination() {
            console.log("checkCombination is working");
            let q = 0;
            let w = 0;
            let e = 0;

            this.colbs.forEach(element => {
                if (element === 81) {
                    q++
                }
                else if (element === 87) {
                    w++
                }
                else if (element === 69) {
                    e++
                }
            });
            console.log("quas: " + this.spells[this.spellIndex].colbs.quas, "wex: " + this.spells[this.spellIndex].colbs.wex, "exort: " + this.spells[this.spellIndex].colbs.exort);
            console.log(this.spells[this.spellIndex].name);
            if (q === this.spells[this.spellIndex].colbs.quas && w === this.spells[this.spellIndex].colbs.wex && e === this.spells[this.spellIndex].colbs.exort) {
                console.log("Combination is correct");
                this.spells.splice(this.spellIndex, 1)
                this.chooseSpell()
            }
        },
        restartGame() {
            this.b = 0
            this.spells = [...spellsData]
            console.log("restartGame", this.spells );
            this.colbs = ['', '', '']
            this.isGameStarted = false
            this.resetStopWatch()
            this.changeImageInColbs()
        },
        onKeyPressed(event) {
            let key = event.keyCode
            if (this.isGameStarted || key === 82 || key === 81 || key === 87 || key === 69) {
                this.registrateClick(key)
            }
        },
        changeImageInColbs() {
            switch (this.colbs[0]) {
                case 81:
                    this.colb1 = "https://invoker-game.com/static/media/invoker_quas.5750837f318a07971a3f.png"
                    break;
                case 87:
                    this.colb1 = "https://invoker-game.com/static/media/invoker_wex.baabeddb7150b37f5752.png"
                    break;
                case 69:
                    this.colb1 = "https://invoker-game.com/static/media/invoker_exort.a56f53208bb284a9d01c.png"
                    break;
                case '':
                    this.colb1 = ""
                    break;
            }
            switch (this.colbs[1]) {
                case 81:
                    this.colb2 = "https://invoker-game.com/static/media/invoker_quas.5750837f318a07971a3f.png"
                    break;
                case 87:
                    this.colb2 = "https://invoker-game.com/static/media/invoker_wex.baabeddb7150b37f5752.png"
                    break;
                case 69:
                    this.colb2 = "https://invoker-game.com/static/media/invoker_exort.a56f53208bb284a9d01c.png"
                    break;
                case '':
                    this.colb2 = ""
                    break;
            }
            switch (this.colbs[2]) {
                case 81:
                    this.colb3 = "https://invoker-game.com/static/media/invoker_quas.5750837f318a07971a3f.png"
                    break;
                case 87:
                    this.colb3 = "https://invoker-game.com/static/media/invoker_wex.baabeddb7150b37f5752.png"
                    break;
                case 69:
                    this.colb3 = "https://invoker-game.com/static/media/invoker_exort.a56f53208bb284a9d01c.png"
                    break;
                case '':
                    this.colb3 = ""
                    break;
            }
        }
    },
    mounted() {
        // Добавляем обработчик событий на объект window или корневой элемент приложения
        window.addEventListener('keydown', this.onKeyPressed);
    },
    destroyed() {
        // Удаляем обработчик событий при размонтировании компонента
        window.removeEventListener('keydown', this.onKeyPressed);
    },
}
</script>

<template>
    <div class="mainSection" @keydown="onKeyPressed" tabindex="0">
        <div class="game" v-if="b === 0">
            <h1 id="title">Invoker Game by Mrvadim91</h1>
            <img src="https://invoker-game.com/static/media/invoker1.d869abaf521e85197572.gif" alt="" id="invokerImg">
            <button class="btnStart" @click="startGame()">Start</button>
        </div>
        <div class="gameStarted" v-if="b === 1">
            <div class="stopWatch">
                <span class="interval">{{ seconds }}</span>
                <span class="colon">.</span>
                <span class="interval">{{ millieseconds }}</span>
            </div>
            <div class="curentSpell">
                <img :src="spellUrl" alt="#">
                <p>{{ spellName }}</p>
            </div>
            <button class="restartGame" @click="restartGame()">
                Restart
            </button>
        </div>
        <div class="gameFinished" v-if="b === 2">
            <h1 id="title">Invoker Game by Mrvadim91</h1>
            <img src="https://invoker-game.com/static/media/invoker1.d869abaf521e85197572.gif" alt="" id="invokerImg">
            <p class="finish">
                Game finished!
            </p>
            <img :src="userRank" alt="">
            <p class="time">{{ seconds }}.{{ millieseconds }} seconds</p>
            <span class="newRecord" v-if="newRecord">New record!</span>
            <button @click="restartGame()">Restart</button>
        </div>
        <ul class="colbs" v-if="b != 2">
            <li><img :src="colb3" alt=""></li>
            <li><img :src="colb2" alt=""></li>
            <li><img :src="colb1" alt=""></li>
        </ul>
        <ul class="skillsList" v-if="b != 2">
            <li class="skill" @click="registrateClick(81)"><img
                    src="https://invoker-game.com/static/media/invoker_quas.5750837f318a07971a3f.png" alt="">
                <span>Q</span>
            </li>
            <li class="skill" @click="registrateClick(87)"><img
                    src="https://invoker-game.com/static/media/invoker_wex.baabeddb7150b37f5752.png" alt="">
                <span>W</span>
            </li>
            <li class="skill" @click="registrateClick(69)"><img
                    src="https://invoker-game.com/static/media/invoker_exort.a56f53208bb284a9d01c.png" alt="">
                <span>E</span>
            </li>
            <li class="skill"><img src="https://invoker-game.com/static/media/no_spell.5ac56c73ca6cbf3b9ac0.png" alt="">
                <span>D</span>
            </li>
            <li class="skill"><img src="https://invoker-game.com/static/media/no_spell.5ac56c73ca6cbf3b9ac0.png" alt="">
                <span>F</span>
            </li>
            <li class="skill" @click="registrateClick(82)"><img
                    src="https://invoker-game.com/static/media/invoker_invoke.a06dc8565470549cac5f.png" alt="">
                <span>R</span>
            </li>
        </ul>
    </div>
</template>

<style scoped>
.gameFinished {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.gameFinished h1 {
    margin-top: 15px;
}

.gameFinished img {
    width: 160px;
    height: 160px;
    margin: 50px auto 0;
}

.gameFinished button {
    background-color: #440b29;
    border: 2px solid #bd925e;
    border-radius: 20px;
    cursor: pointer;
    font-size: 25px;
    font-weight: 700;
    height: 50px;
    margin-top: 40px;
    width: 200px;
    margin-bottom: 10px;
}

.time {
    font-size: 40px;
    margin-top: 30px;
}

.finish {
    margin: 50px auto 10px auto;
    font-size: 24px;
}

.game {
    display: flex;
    flex-direction: column;
}

.mainSection {
    background-color: #141313;
    border-radius: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, .5);
    margin: 0 20px;
    display: flex;
    flex-direction: column;
}

h1 {
    text-align: center;
    margin: 0;
    margin-top: 50px;
}

#invokerImg {
    margin: 10px auto 0 auto;
    height: 170px;
    width: 300px;
}

.btnStart {
    margin-left: auto;
    margin-right: auto;
    margin-top: 40px;
    width: 200px;
    background-color: #440b29;
    border: 2px solid #bd925e;
    border-radius: 20px;
    cursor: pointer;
    font-size: 25px;
    font-weight: 700;
}

.colbs {
    display: flex;
    justify-content: center;
    list-style: none;
    margin: 50px auto 0;
}

.colbs li {
    box-shadow: 0 0 10px rgba(0, 0, 0, .5);
    display: flex;
    height: 100px;
    justify-content: center;
    margin-left: 20px;
    margin-right: 20px;
    width: 100px;
    align-items: center;
    border-radius: 100px;
    overflow: hidden;
}

.skillsList {
    display: flex;
    list-style: none;
    justify-content: space-around;
}

.skill {
    position: relative;
    border: 5px groove #1d1c1c;
    padding: 5px;
    margin-right: 10px;
    display: flex;
    cursor: pointer;
}

.skill:last-child {
    margin-right: 0;
}

.skillsList span {
    position: absolute;
    z-index: 3;
    right: 10px;
}

.skill img {
    width: 90px;
    height: 90px;
}

.gameStarted {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.restartGame {
    align-items: center;
    background-color: #141313;
    border: none;
    border-radius: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, .5);
    cursor: pointer;
    display: flex;
    font-size: 18px;
    height: 40px;
    justify-content: space-around;
    margin-left: auto;
    margin-right: auto;
    margin-top: 20px;
    padding: 15px;
    width: 200px;
}

.stopWatch {
    font-size: 60px;
    margin: 70px 0;
}
</style>