<script setup>
import { ref } from 'vue'
import { reactive } from 'vue'

const dice = reactive([
  { diceNumber: 1, number: 0 },
  { diceNumber: 2, number: 0 },
  { diceNumber: 3, number: 0 },
  { diceNumber: 4, number: 0 },
  { diceNumber: 5, number: 0 },
  { diceNumber: 6, number: 0 },
])

const counts = reactive([
  { dice: 1, sum: 0 },
  { dice: 2, sum: 0 },
  { dice: 3, sum: 0 },
  { dice: 4, sum: 0 },
  { dice: 5, sum: 0 },
  { dice: 6, sum: 0 },
])

const one = reactive(0);
const two = reactive(0);
const three = reactive(0);
const four = reactive(0);
const five = reactive(0);
const six = reactive(0);
const total = reactive(0);
const totalUnderHalf = reactive(0);

const threeOfaKind = reactive(0);
const fourOfaKind = reactive(0);
const fiveOfAkind = reactive(0);
const fullHouse = reactive(0);
const chance = reactive(0);
const smallStreet = reactive(0);
const bigStreet = reactive(0);

const rollDice = () => {
  for (const number in dice) {
    dice[number].number = 0
  }
  for (let i = 0; i <= 7; i++) {
    const diceRolls = Math.floor((Math.random() * 6) + 1);
    dice[i].number = diceRolls
  }

}



</script>


<template>
  <table>
    <tbody>
      <tr v-for="(numbers, index) in dice" :key="index">
        {{ numbers.number }}
      </tr>
    </tbody>
  </table>
  <button @click="rollDice()">Gooien!</button>
  <table>
    <thead>
      <tr>
        <th>Deel 1</th>
        <th>Punten telling</th>
        <th>1e spel</th>
        <th>2e spel</th>
        <th>3e spel</th>
        <th>4e spel</th>
        <th>5e spel</th>
        <th>6e spel</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Enen</td>
        <td>Tel alle Enen</td>
        <td>{{ one }}</td>
      </tr>
      <tr>
        <td>Tweeën</td>
        <td>Tel alle Tweeën</td>
        <td>{{ two }}</td>
      </tr>
      <tr>
        <td>Drieën</td>
        <td>Tel alle Drieën</td>
        <td>{{ three }}</td>
      </tr>
      <tr>
        <td>Vieren</td>
        <td>Tel alle Vieren</td>
        <td>{{ four }}</td>
      </tr>
      <tr>
        <td>Vijven</td>
        <td>Tel alle Vijven</td>
        <td> {{ five }}</td>
      </tr>
      <tr>
        <td>Zessen</td>
        <td>Tel alle Zessen</td>
        <td> {{ six }}</td>
      </tr>
      <tr>
        <td>Totaal aantal punten</td>
        <td></td>
        <td> {{ total }}</td>
      </tr>
    </tbody>
  </table>
  <table>
    <thead>
      <tr>
        <th>Deel 2</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Three of a kind</td>
        <td>3 dezelfde Totaal v.d. 5 stenen </td>
        <td>{{ threeOfaKind }}</td>
      </tr>
      <tr>
        <td>Carré</td>
        <td>4 dezelfde Totaal v.d. 5 stenen </td>
        <td>{{ fourOfaKind }}</td>
      </tr>
      <tr>
        <td>Full House</td>
        <td>2 + 3 dezelfde 25 punten</td>
        <td>{{ fullHouse }}</td>
      </tr>
      <tr>
        <td>Kleine straat</td>
        <td>4 opeenvolgende nummers 30 punten</td>
        <td>{{ smallStreet }}</td>
      </tr>
      <tr>
        <td>Grote straat</td>
        <td>5 opeenvolgende nummers 40 punten</td>
        <td>{{ bigStreet }}</td>
      </tr>
      <tr>
        <td>Topscore</td>
        <td>5 dezelfde 50 punten</td>
        <td>{{ fiveOfAkind }} </td>
      </tr>
      <tr>
        <td>Kans</td>
        <td>vrije keus Totaal v.d. 5 stenen</td>
        <td>{{ chance }}</td>
      </tr>
      <tr>
        <td>Totaal</td>
        <td>van de onderste helft</td>
        <td> {{ totalUnderHalf }}</td>
      </tr>
      <tr>
        <td>Totaal</td>
        <td>van de bovenste helft</td>
        <td>{{ total }}</td>
      </tr>
      <tr>
        <td>Totaal Generaal</td>
        <td></td>
        <td> {{ total + totalUnderHalf }} </td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped></style>
