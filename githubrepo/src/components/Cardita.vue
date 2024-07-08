<script setup lang="ts">
import { ref } from "vue";

defineProps<{
  nameproyect: string;
  fullnameproyect: string;
  languageproyect: string;
  fechaproyect: string;
}>();

const count = ref(0);
</script>

<template>
  <div class="col mb-4">
    <div class="container" style="display: flex; justify-content: center">
      <div class="card p-3">
        <figure class="p-3 mb-0">
          <blockquote class="blockquote">
            <center>
              <strong
                ><p id="texto">{{ nameproyect }}</p></strong
              >
            </center>
          </blockquote>
          <p id="nombrecp">
            <strong>- Name Complete:</strong> {{ fullnameproyect }}
          </p>
          <p id="lenguaje">
            <strong>- Language:</strong> {{ languageproyect }}
          </p>
          <p id="consejo"><strong>- Updated at:</strong> {{ fechaproyect }}</p>
        </figure>
        <div style="display: flex; justify-content: center">
          <button id="boton" type="button" class="btn btn-secondary">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="16"
              height="16"
              fill="currentColor"
              class="bi bi-arrow-clockwise"
              viewBox="0 0 16 16"
            >
              <path
                fill-rule="evenodd"
                d="M8 3a5 5 0 1 0 4.546 2.914.5.5 0 0 1 .908-.417A6 6 0 1 1 8 2z"
              ></path>
              <path
                d="M8 4.466V.534a.25.25 0 0 1 .41-.192l2.36 1.966c.12.1.12.284 0 .384L8.41 4.658A.25.25 0 0 1 8 4.466"
              ></path>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
