<script setup>

</script>

<template>
    <div class="controlls">
        <h3>Controlls</h3>
        <ul id="controlls">
            <li><img src="https://invoker-game.com/static/media/invoker_quas.5750837f318a07971a3f.png" alt="">
                <p>Q - Quas</p>
            </li>
            <li><img src="https://invoker-game.com/static/media/invoker_wex.baabeddb7150b37f5752.png" alt="">
                <p>W - Wex</p>
            </li>
            <li><img src="https://invoker-game.com/static/media/invoker_exort.a56f53208bb284a9d01c.png" alt="">
                <p>E - Exort</p>
            </li>
            <li><img src="https://invoker-game.com/static/media/no_spell.5ac56c73ca6cbf3b9ac0.png" alt="">
                <p>D - Spell 1</p>
            </li>
            <li><img src="https://invoker-game.com/static/media/no_spell.5ac56c73ca6cbf3b9ac0.png" alt="">
                <p>F - Spell 2</p>
            </li>
            <li><img src="https://invoker-game.com/static/media/invoker_invoke.a06dc8565470549cac5f.png" alt="">
                <p>R - Invoke</p>
            </li>
        </ul>
    </div>
        
</template>

<style scoped>
    .controlls {
        background-color: #141313;
        border-radius: 20px;
        width: 300px;
        padding: 15px;
        text-align: center;         
    }

    .controlls img {
        width: 70px;
    }

  #controlls li{
    display: flex;
    margin-bottom: 20px;
    align-items: center;
  }
  #controlls li p{
    margin-left: 15px;
  }

  .controlls h3 {
    margin: 0 auto;
  }

</style>