
<script setup>
import { ref, computed } from 'vue'

const nouvelleTache = ref('')

const taches = ref([])
let prochainId = 1

function ajouterTache() {
  if (nouvelleTache.value.trim() !== '') {
    taches.value.push({
      id: prochainId,
      texte: nouvelleTache.value.trim(),
      terminee: false
    })

    prochainId++
    nouvelleTache.value = ''
  }
}

function supprimerTache(id) {
  taches.value = taches.value.filter(tache => tache.id !== id)
}

const tachesRestantes = computed(() => {
  return taches.value.filter(tache => !tache.terminee).length
})
</script>

<template>
  <div class="application">
    <h1>Gestion des tâches</h1>

    <form @submit.prevent="ajouterTache">
      <input
        v-model="nouvelleTache"
        type="text"
        placeholder="Entrez une nouvelle tâche"
      >

      <button type="submit">Ajouter</button>
    </form>

    <h3>Tâches restantes : {{ tachesRestantes }}</h3>

    <p v-if="taches.length === 0">
      Aucune tâche pour le moment.
    </p>

    <ul v-else>
      <li v-for="tache in taches" :key="tache.id">
        <label>
          <input type="checkbox" v-model="tache.terminee">

          <span :class="{ terminee: tache.terminee }">
            {{ tache.texte }}
          </span>
        </label>

        <button @click="supprimerTache(tache.id)">
          Supprimer
        </button>
      </li>
    </ul>
  </div>
</template>

<style>
.application {
  max-width: 600px;
  margin: 60px auto;
  padding: 25px;
  font-family: Arial, sans-serif;
  background: white;
  border-radius: 12px;
  box-shadow: 0 2px 12px #cccccc;
}

h1 {
  text-align: center;
  color: #35495e;
}

form {
  display: flex;
  gap: 10px;
}

form input {
  flex: 1;
  min-width: 0;
  padding: 10px;
}

button {
  padding: 10px 14px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  background: #42b883;
  color: white;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 10px;
  margin: 12px 0;
}

.terminee {
  text-decoration: line-through;
  color: gray;
}
</style>