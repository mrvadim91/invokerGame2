<script >
export let keyBindsArr = [81, 87, 69, 82]
let reserve = [...keyBindsArr]

export default {
  data() {
    return {
      a: 0
    }
  },
  methods: {
    changeBind(whatToChange, event) {
      keyBindsArr[whatToChange] = event.keyCode
      console.log(keyBindsArr[whatToChange]);
      this.a = 0
      window.removeEventListener('keydown', this.changeBind);
    },
    getKey(whatToChange) {
      this.a = 1;
      // Сохраняем ссылку на анонимную функцию для удаления слушателя позже
      let listener = (event) => this.changeBind(whatToChange, event);
      window.addEventListener('keydown', listener);
      // Удаление слушателя после вызова
      window.addEventListener('keyup', () => {
        window.removeEventListener('keydown', listener);
      });
    },
    resetBinds() {
      keyBindsArr = [...reserve]
    }
  }
}
</script>

<template>
  <div class="whenChangeBinds" v-if="a != 0">
    <p>fck</p>
  </div>
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
        <div class="keybinds1">
            <p>Set keybinds</p>
            <button @click="resetBinds()">Reset</button>
        </div>
        <div class="keybinds2">
            <button @click="getKey(0)">Quas</button>
            <button @click="getKey(1)">Wex</button>
            <button @click="getKey(2)">Exort</button>
            <button @click="getKey(3)">Invoke</button>
        </div>
    </div>
        
</template>

<style scoped>

.whenChangeBinds{
  width: 98vw;
  height: 98vh;
  text-align: center;
  display: flex;
  align-items: center;
  justify-self: center;  
  background-color: #000;
  position: absolute;
  opacity: 0.33;
  font-size: 40px;
}

.whenChangeBinds p{
  margin: 0 auto;
}
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

  .controlls div{
    display: flex;
  }

  button{
    background-color: #141313;
    border: 3px groove #000;
    cursor: pointer;
    padding: 3px;
  }

  .keybinds2{
    margin-top: 15px;
    justify-content: space-between;
  }

  .keybinds1 p {
    font-size: 19px;
    margin-right: 7px;
  }

  .keybinds1{
    align-items: center;
  }

</style>