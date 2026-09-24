<script lang="ts" setup>
/**
 * Kernkonzept: Listen rendern mit v-for. buecher ist ein normales Array von
 * Objekten, wie aus den TypeScript-Übungen bekannt. v-for="buch in buecher"
 * im Template (unten) erzeugt für jedes Element automatisch ein <li>, ohne
 * manuelles forEach + createElement/appendChild wie noch bei den
 * DOM-Übungen.
 */
const buecher = [
  { id: 1, titel: "Der Herr der Ringe", autor: "J.R.R. Tolkien" },
  {
    id: 2,
    titel: "Harry Potter und der Stein der Weisen",
    autor: "J.K. Rowling",
  },
  { id: 3, titel: "Die Chroniken von Narnia", autor: "C.S. Lewis" },
  { id: 4, titel: "Der Hobbit", autor: "J.R.R. Tolkien" },
  { id: 5, titel: "Die Tribute von Panem", autor: "Suzanne Collins" },
  { id: 6, titel: "Percy Jackson – Diebe im Olymp", autor: "Rick Riordan" },
  { id: 7, titel: "Die Bestimmung", autor: "Veronica Roth" },
];
</script>

<template>
  <div>
    <h2>Bücherliste</h2>
    <ul>
      <!-- :key="buch.id" ist Pflicht bei v-for: eine eindeutige,
           stabile Kennung pro Element, damit Vue bei Änderungen am Array
           jedes <li> wiedererkennt, statt bei jeder Änderung alles neu
           zu bauen. id eignet sich hier besser als titel, falls zwei
           Bücher zufällig denselben Titel hätten. -->
      <li v-for="buch in buecher" :key="buch.id">
        {{ buch.titel }} von {{ buch.autor }}
      </li>
    </ul>
  </div>
</template>
