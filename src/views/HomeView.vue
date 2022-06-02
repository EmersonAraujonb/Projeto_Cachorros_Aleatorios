<template>
  <div class="home">
    <h1 class="title">Cachorros Aleatórios</h1>
    <div class="container">
      <button id="botao" @click="Aleatorio">Aleatório</button>
      <button id="botao2" @click="Atualizar">
        Atualizar página para ver outro cachorro!
      </button>
    </div>
    <p class="imgDog"></p>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  mounted() {
    document.getElementById("botao2").disabled = true;
  },
  methods: {
    Aleatorio() {
      let url = "https://dog.ceo/api/breeds/image/random";
      const request = fetch(url);
      request
        .then(function (response) {
          const data = response.json();
          return data;
        })
        .then(function (processedResponse) {
          console.log(processedResponse);
          const img = document.createElement("img");
          img.src = processedResponse.message;
          document.querySelector(".imgDog").appendChild(img);
        });
      document.getElementById("botao").disabled = true;
      document.getElementById("botao2").disabled = false;
    },
    Atualizar() {
      setTimeout((Aleatorio) => {
        document.location.reload(true);
      }, 1000);
    },
  },
};
</script>
<style scoped>
.home {
  background-color: rgb(191, 191, 191);
  height: 900px;
  align-content: center;
  align-items: center;
  align-content: space-around;
}
.title {
  font-size: 30pt;
  color: black;
  text-shadow: 10px 10px 6.5px rgb(59, 59, 59);
}
.container {
  font-family: ubuntu mono, monospace;
  padding: 1px;
  display: inline-block;
  height: 40px;
}
#botao {
  background-color: rgb(0, 191, 255);
  width: 80px;
  height: 40px;
  display: inline-block;
  border: none;
  margin: 30px;
  box-shadow: 5px 7px 3px 0 #00000080;
}
#botao2 {
  background-color: rgb(0, 191, 255);
  width: 300px;
  height: 40px;
  display: inline-block;
  border: none;
  margin: 30px;
  left: 300px;
  box-shadow: 5px 7px 3px 0 #00000080;
}
#botao:hover {
  background-color: rgb(0, 255, 0);
  transition-delay: 0.1s;
  border-radius: 30px;
}
#botao2:hover {
  background-color: rgb(255, 170, 0);
  transition-delay: 0.1s;
  border-radius: 30px;
}
.p {
  display: flex;

  margin-left: 300px;
  margin-right: 100px;
  
}
</style>
