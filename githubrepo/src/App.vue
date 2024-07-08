<script setup lang="ts">
import HelloWorld from "./components/HelloWorld.vue";
import Cardita from "./components/Cardita.vue";
import { ref } from "vue";
const p = ref(0);
const i = 4;
const inputValue = ref("");
const urla = ref("");
const nombreproyecto = ref("");
const nombrecompleto = ref("");
const languageprog = ref("");
const urlproyecto = ref("");
const fechaproyecto = ref("");
const ownerproyecto = ref("");
const pablo = ref("");

const usuario = ref("");

async function fetchData(url: string): Promise<any> {
  const response = await fetch(url);

  if (!response.ok) {
    throw new Error(`HTTP error! status: ${response.status}`);
  }

  const data = await response.json();
  return data;
}

async function fetchData1(url: string, i: number): Promise<any> {
  const response = await fetch(url);

  if (!response.ok) {
    throw new Error(`HTTP error! status: ${response.status}`);
  }

  const data = await response.json();
  return data;
}

fetchData("https://api.github.com/users/olhacodes/repos")
  .then((data) => {
    console.log(data);
    pablo.value = data;
    console.log(data[i]["name"]);
    console.log(data[i]["full_name"]);
    console.log(data[i]["language"]); //sourceUrls
    console.log(data[i]["url"]);
    console.log(data[i]["updated_at"]);
    console.log(data[i]["owner"]["login"]);
    nombreproyecto.value = data[0]["name"];
    nombrecompleto.value = data[0]["full_name"];
    languageprog.value = data[0]["language"];
    urlproyecto.value = data[0]["owner"]["html_url"];
    fechaproyecto.value = data[0]["updated_at"];
    ownerproyecto.value = data[0]["owner"]["login"];
  })
  .catch((error) => {
    console.error(error);
    alert("No se encontro el perfil");
  });

fetchData1("https://api.github.com/users/olhacodes/repos", i)
  .then((data) => {
    console.log(data);
    pablo.value = data;
    console.log(data[i]["name"]);
    console.log(data[i]["full_name"]);
    console.log(data[i]["language"]); //sourceUrls
    console.log(data[i]["url"]);
    console.log(data[i]["updated_at"]);
    console.log(data[i]["owner"]["login"]);
    nombreproyecto.value = data[0]["name"];
    nombrecompleto.value = data[0]["full_name"];
    languageprog.value = data[0]["language"];
    urlproyecto.value = data[0]["owner"]["html_url"];
    fechaproyecto.value = data[0]["updated_at"];
    ownerproyecto.value = data[0]["owner"]["login"];
  })
  .catch((error) => {
    console.error(error);
    alert("No se encontro el perfil");
  });

function cambiapalabra() {
  console.log("dfsdfsd");
  fetchData1("https://api.github.com/users/" + this.inputValue + "/repos", 2)
    .then((data) => {
      pablo.value = data;
      console.log(data);
      console.log(data[0]["name"]);
      console.log(data[0]["full_name"]);
      console.log(data[0]["language"]); //sourceUrls
      console.log(data[0]["url"]);
      console.log(data[0]["updated_at"]);
      console.log(data[0]["owner"]["login"]);
      nombreproyecto.value = data[0]["name"];
      nombrecompleto.value = data[0]["full_name"];
      languageprog.value = data[0]["language"];
      urlproyecto.value = data[0]["owner"]["html_url"];
      fechaproyecto.value = data[0]["updated_at"];
      ownerproyecto.value = data[0]["owner"]["login"];
    })
    .catch((error) => {
      console.error(error);
      alert("No se encontro el perfil");
    });
}
function goToNewPage() {
  window.location.href = urlproyecto.value; // Replace with your target URL
}
function linkeo(p) {
  window.location.href =
    "https://github.com/" +
    this.pablo[p]["owner"]["login"] +
    "/" +
    this.pablo[p]["name"]; // Replace with your target URL
}
</script>

<template>
  <h1>GitHub Profiles Repository</h1>

  <div class="input-group mb-3 mt-5">
    <input
      v-model="inputValue"
      type="text"
      class="form-control"
      placeholder="Write the word"
      aria-label="word"
      aria-describedby="basic-addon1"
    />
    <button
      @click.prevent="cambiapalabra()"
      type="button"
      class="btn btn-secondary"
    >
      <i class="bi bi-search"></i>
    </button>
  </div>
  <!--h6>{{ nombreproyecto }}</h6>
  <h6>-Name Complete: {{ nombrecompleto }}</h6>
  <h6>-Language: {{ languageprog }}</h6>
  <h6>-URL: {{ urlproyecto }}</h6>
  <h6>-Fecha Proyecto: {{ fechaproyecto }}</h6>
  <h6>-Author: {{ ownerproyecto }}</h6>
  <h6>-Data: {{ pablo[0]["owner"]["login"] }}</h6-->

  <div class="container">
    <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3">
      <div v-for="n in 6" class="col mb-4">
        <div class="container" style="display: flex; justify-content: center">
          <div class="card p-3">
            <figure class="p-3 mb-0">
              <blockquote class="blockquote">
                <center>
                  <strong
                    ><p id="texto">{{ pablo[n]["name"] }}</p></strong
                  >
                </center>
              </blockquote>

              <p id="lenguaje">
                <strong>- Language:</strong> {{ pablo[n]["language"] }}
              </p>
              <p id="consejo">
                <strong>- Updated at:</strong> {{ pablo[n]["updated_at"] }}
              </p>
              <p id="conseja">
                <strong>- Author:</strong> {{ pablo[n]["owner"]["login"] }}
              </p>
            </figure>
            <div style="display: flex; justify-content: center">
              <button
                @click="linkeo(n)"
                id="boton"
                type="button"
                class="btn btn-secondary"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="16"
                  height="16"
                  fill="currentColor"
                  class="bi bi-share"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M13.5 1a1.5 1.5 0 1 0 0 3 1.5 1.5 0 0 0 0-3M11 2.5a2.5 2.5 0 1 1 .603 1.628l-6.718 3.12a2.5 2.5 0 0 1 0 1.504l6.718 3.12a2.5 2.5 0 1 1-.488.876l-6.718-3.12a2.5 2.5 0 1 1 0-3.256l6.718-3.12A2.5 2.5 0 0 1 11 2.5m-8.5 4a1.5 1.5 0 1 0 0 3 1.5 1.5 0 0 0 0-3m11 5.5a1.5 1.5 0 1 0 0 3 1.5 1.5 0 0 0 0-3"
                  />
                </svg>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <button type="button" class="btn btn-dark" @click="goToNewPage()">
      Click for more details
    </button>
  </div>

  <!--HelloWorld msg="Vite + Vue" /-->
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
#texto {
  font-size: 18px;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
