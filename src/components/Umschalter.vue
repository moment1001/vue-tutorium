<script lang="ts" setup>
/**
 * Kernkonzept: Bedingtes Rendern mit v-if. isVisible ist ein ref(), genau
 * wie zaehler in Zaehler.vue, nur mit einem boolean statt einer number.
 * Im Template entscheidet v-if="isVisible" (unten am div), ob das Element
 * überhaupt ins DOM eingefügt wird: bei false existiert es dort gar nicht,
 * anders als bei v-show, das das Element behält und nur per CSS
 * (display: none) versteckt.
 */
import { ref } from "vue";
const isVisible = ref(true);
const toggleVisibility = () => {
  isVisible.value = !isVisible.value;
};
</script>

<template>
  <!-- Der Ternary-Ausdruck isVisible ? "..." : "..." ist reines JavaScript,
       kein Vue-Feature: Vue wertet innerhalb von {{ }} normale JS-Ausdrücke
       aus, deshalb funktioniert der aus den JS-Grundlagen bekannte
       Bedingungsoperator hier genauso wie im Script. -->
  <button @click="toggleVisibility">
    {{ isVisible ? "Inhalt ausblenden" : "Inhalt einblenden" }}
  </button>
  <div v-if="isVisible">
    <p>Inhalt, der umgeschaltet wird.</p>
  </div>
</template>
