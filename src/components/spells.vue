<script setup>

</script>

<template>
    <div class="spells">
        <h3>Spells</h3>
        <ul class="spellsList">
            <li class="spell"><img src="https://i.imgur.com/ybyy7Nc.png" alt="">
                <p>Cold Snap - Q Q Q</p>
            </li>
            <li class="spell"><img src="https://i.imgur.com/7OrGjum.png" alt="">
                <p>Ghost Walk - Q Q W</p>
            </li>
            <li class="spell"><img src="https://i.imgur.com/86LdpGf.png" alt="">
                <p>Ice Wall - Q Q E</p>
            </li>
            <li class="spell"><img src="https://i.imgur.com/uKdTgNA.png" alt="">
                <p>EMP - W W W</p>
            </li>
            <li class="spell"><img src="https://i.imgur.com/i1KCylk.png" alt="">
                <p>Tornado - W W Q</p>
            </li>
            <li class="spell"><img src="https://i.imgur.com/XV6jrjn.png" alt="">
                <p>Alacrity - W W E</p>
            </li>
            <li class="spell"><img src="https://i.imgur.com/BKfGS1j.png" alt="">
                <p>Sun Strike - E E E</p>
            </li>
            <li class="spell"><img src="https://i.imgur.com/NxuYJSS.png" alt="">
                <p>Forge Spirit - E E Q</p>
            </li>
            <li class="spell"><img src="https://i.imgur.com/6ls7uCX.png" alt="">
                <p>Chaos Meteor - E E W</p>
            </li>
            <li class="lust"><img src="https://i.imgur.com/w2uWA7c.png" alt="">
                <p>Deafening Blast - Q W E</p>
            </li>
        </ul>
    </div>
</template>

<style scoped>
.spellsList li {
    display: flex;
    align-items: center;
    height: 50px;
    flex-direction: row;    
}

.spell {
    margin-bottom: 20px;
}

.last {
    margin: 1px;
}

.spellsList p {
    margin-left: 20px;
}

.spells {
    background-color: #141313;
    display: flex;
    text-align: center;
    flex-direction: column;
    align-items: center;
    border-radius: 20px;
    height: fit-content;
    padding: 15px;
    padding-bottom: 0;
}

h3 {
    margin: 0;
}

ul {
    margin-bottom: 0;
}


</style>