<script setup lang="ts">
/**
 * Kernkonzept: Reaktive Daten mit ref(). zaehler ist kein einfacher Wert,
 * sondern ein reaktives Objekt, dessen eigentlicher Inhalt in .value
 * liegt. Ändert sich zaehler.value, aktualisiert Vue automatisch alle
 * Stellen im Template, die den Wert anzeigen, ohne manuelles DOM-Update
 * wie früher bei document.querySelector/.textContent.
 *
 * Stolperstein/Merkpunkt: .value wird nur im Script gebraucht. Im
 * Template (siehe unten, {{ zaehler }}) entpackt Vue den ref automatisch,
 * dort würde zaehler.value sogar einen Fehler geben.
 */
import { ref } from "vue";

const zaehler = ref(0);

function erhoehen() {
  zaehler.value++;
}
</script>

<template>
  <!-- @click ist die Kurzschreibweise für v-on:click, Vues Pendant zu
       addEventListener: bei Klick wird die Funktion erhoehen aufgerufen. -->
  <button @click="erhoehen">Zähler: {{ zaehler }}</button>
</template>

<style scoped>
button {
  font-size: 1.2rem;
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 4px;
  background-color: #42b983;
  color: white;
  cursor: pointer;
}
</style>
