<!-- JSONLab.vue -->
<template>
  <div class="json-lab">
    <h1>🗄️ JSON Data & Vue Directives Lab</h1>
    <ul>
      <li v-for="author in authors" :key="author.id">{{ author.name }} ({{ author.birthYear }})</li>
    </ul>
    <ul>
      <li v-for="author in modernAuthors" :key="author.id">
        {{ author.name }} ({{ author.birthYear }})
      </li>
    </ul>
    <ul>
      <li v-for="work in allFamousWorks" :key="work">
        {{ work }}
      </li>
    </ul>

    <button @click="showMessage = !showMessage">Toggle Message</button>
    <p v-if="showMessage" class="message success">✨ You're a Vue superstar! ✨</p>
    <p v-else class="message">Click the button to see a message.</p>

    <ul>
      <li
        v-for="(author, index) in authors"
        :key="author.id"
        :class="{ highlight: index % 2 === 0 }"
      >
        {{ author.name }} ({{ author.birthYear }})
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import authors from '../assets/json/authors.json'
import bookstores from '../assets/json/bookstores.json'

// Activity 1: Import JSON files (authors.json and bookstores.json)
// TODO: CODE TO IMPORT JSON FILES HERE

const showMessage = ref(false)

// Activity 2: Get authors born after 1850
const modernAuthors = computed(() => {
  // TODO: CODE TO FILTER ARRAY OF AUTHORS HERE
  authors.filter((author) => author.birthYear > 1850)
})

// Activity 3: Get all famous works
const allFamousWorks = computed(() => {
  // TODO: CODE TO GET ALL FAMOUS WORKS HERE
  // authors.filter((author) => author.birthYear > 1850)
  authors.flatMap((author) => author.famousWorks.map((work) => work.title))
})

// Activity 4: Find author by name
const orwell = computed(() => {
  // TODO: CODE TO FIND AUTHOR BY NAME HERE
})

// Activity 5: Find author by ID
const austen = computed(() => {
  // TODO: CODE TO FIND AUTHOR BY ID HERE
})
</script>

<style scoped>
.highlight {
  background-color: #e66cbd;
  font-weight: bold;
}
.json-lab {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  max-width: 80vw;
  margin: 0 auto;
  padding: 20px;
  background-color: #f4f4f4;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

h1,
h2 {
  color: #333;
}
h1 {
  text-align: center;
}

.lab-section {
  background-color: white;
  padding: 20px;
  margin-bottom: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.message {
  padding: 10px;
  border-radius: 5px;
  margin-top: 10px;
}

.success {
  background-color: #e7faf3;
  color: #42b883;
  border: 1px solid #42b883;
}

.highlight {
  background-color: #42b883;
}

code {
  background-color: #e0e0e0;
  padding: 2px 5px;
  border-radius: 4px;
  font-family: 'Courier New', Courier, monospace;
}

ul {
  list-style-type: none;
  padding: 0;
}
li {
  background-color: #f0f0f0;
  padding: 10px;
  margin: 5px 0;
  border-radius: 5px;
}
</style>
