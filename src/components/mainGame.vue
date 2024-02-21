<script setup>

</script>

<template>
    <div class="mainSection">
        <h1 id="title">Invoker Game by Mrvadim91</h1>
        <img src="https://invoker-game.com/static/media/invoker1.d869abaf521e85197572.gif" alt="" id="invokerImg">
        <button class="btnStart">Start</button>

        <ul class="colbs">
            <li></li>
            <li></li>
            <li></li>
        </ul>
        <ul class="skillsList">
            <li class="skill"><img src="https://invoker-game.com/static/media/invoker_quas.5750837f318a07971a3f.png"
              alt=""> <span>Q</span></li>
          <li class="skill"><img src="https://invoker-game.com/static/media/invoker_wex.baabeddb7150b37f5752.png"
              alt=""> <span>W</span></li>
          <li class="skill"><img src="https://invoker-game.com/static/media/invoker_exort.a56f53208bb284a9d01c.png"
              alt=""> <span>E</span></li>
          <li class="skill"><img src="https://invoker-game.com/static/media/no_spell.5ac56c73ca6cbf3b9ac0.png" alt="">
            <span>D</span></li>
          <li class="skill"><img src="https://invoker-game.com/static/media/no_spell.5ac56c73ca6cbf3b9ac0.png" alt="">
            <span>F</span></li>
          <li class="skill"><img src="https://invoker-game.com/static/media/invoker_invoke.a06dc8565470549cac5f.png"
              alt=""> <span>R</span></li>
        </ul>
    </div>
</template>

<style scoped>
.mainSection{
    background-color: #141313;
    border-radius: 20px;
    box-shadow: 0 0 10px rgba(0,0,0,.5);
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
    box-shadow: 0 0 10px rgba(0,0,0,.5);
    display: flex;
    height: 100px;
    justify-content: center;
    margin-left: 20px;
    margin-right: 20px;
    width: 100px;
    align-items: center;
    border-radius: 100px;
}

.skillsList {
    display: flex;
    list-style: none;
    justify-content: space-around;
}

.skill{
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


</style>