<script>
import BenderStatistics from './components/BenderStatistics.vue';
import Counter from './components/Counter.vue';
import NameList from './components/NameList.vue';
import UserCard from './components/UserCard.vue';

export default {
  components: {
    Counter,
    NameList,
    BenderStatistics,
    UserCard
},
  data: () => ({
    userData: {
      name: 'Henry',
      preferedFramework: 'next',
      favoriteFood: 'steak',
      favoriteNumber: [24,12]
    },
    newCharacter: {
      name: "",
      element: [],
    },
    characterList: [
      {
        name: "Aang",
        element: ["Air", "Earth", "Water", "Fire"],
      },
      {
        name: "Zuko",
        element: ["Fire"],
      },
      {
        name: "Toph",
        element: ["Earth"],
      },
      {
        name: "Katara",
        element: ["Water"],
      },
    ],
    favoriteList: [],
  }),
  methods: {
    addNewCharacter() {
      this.characterList.push(this.newCharacter);
      this.newCharacter = { name: "" };
    },
    favoriteCharacter(character) {
      this.favoriteList.push(character);
    },

    incrementCount(newAmount, event) {
      console.log(newAmount)
      console.log(event)
      this.count += this.optimizedIncrementAmount
    },

    changeName() {
      this.userData.name = "Henry"
    }
  },
  computed: {
    refinedUserData() {
      return {
        name: this.userData.name,
        food: this.userData.favoriteFood      
      }
    }
  }
}
</script>

<template>
  <UserCard :user="refinedUserData" @change-name="changeName"/>
  <NameList />
  <hr>
  <Counter :increment="incrementCount"/>
  <hr>
  <BenderStatistics :characters="characterList" />
  <hr>
  <h2>Characters</h2>
  <p v-if="characterList.length === 0">There are no characters</p>
  <ul v-else-if="characterList.length % 2 === 0">
    <li v-for="(character, index) in characterList" :key="`even-character${index}`">
      <p>{{ character.name }}</p>
      <button @click="favoriteCharacter(character)">⭐ Favorite</button>
    </li>
  </ul>
  <h2>Favorite Characters</h2>
  <ul v-if="favoriteList.length > 0">
    <li v-for="(character, index) in favoriteList" :key="`odd-character${index}`">
      {{ character }}
    </li>
  </ul>
  <p v-else>No favorite characters yet!</p>
  <h2>New Character</h2>
  <pre>{{ newCharacter }}</pre>
  <label for="character-name">Name</label>
  <input type="text" v-model="newCharacter.name" @keyup.enter="addNewCharacter" />
  <p>
    <span v-for="(character, index) in characterList" :key="`comma-list-character-${index}`">
      {{ character.name }}{{ index === characterList.length - 1 ? '' : ',' }}
    </span>
  </p>
</template>
