<template>

  <div id="app">
    <v-card
      class="mx-auto"
      max-width="344"
    >

      <v-app-bar
        dark
        color="#ccc"
      >
        <v-toolbar-title>Dolar Atual</v-toolbar-title>
        <v-spacer></v-spacer>

      </v-app-bar>
      <v-img
        src="https://image.freepik.com/fotos-gratis/sinal-de-dolar-simbolo_2227-466.jpg"
        aspect-ratio="1"
      ></v-img>

      <v-card-title primary-title>
        <div>
          <h3 class="headline mb-0">Dolar em Reais </h3>
          <p
            v-for="dado in card_text"
            :key="dado.id"
          > {{ dado.bid }} </p>
        </div>
      </v-card-title>
      <v-card-actions>
        <v-btn
          color="#6959CD"
          text
          @click="carregarDados"
        >
          Atualizar
        </v-btn>
      </v-card-actions>
    </v-card>
  </div>

</template>

<script>
export default {
  data () {
    return {
      card_text: []
    }
  },
  methods: {
    async carregarDados () {
      const urlApi = `http://economia.awesomeapi.com.br/json/all/USD-BRL`
      this.card_text = await fetch(urlApi).then(res => res.json())
    }
  },
}
</script>

<style>
#button {
  align-items: center;
}
</style>