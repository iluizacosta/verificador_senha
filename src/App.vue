<script setup lang="ts">
import { computed, ref } from 'vue';

const senha = ref('')

const contarSenha = computed(() => {
  return senha.value.length
})

</script>

<template>
  <div class="container">
    <div class="cabecalho">
      <h1>Verificador de Senha</h1>
    </div>

    <div class="label">
      <label>Digite sua senha: </label>
    </div>

    <div class="inputSenha">
      <input type="password" v-model="senha"></input>
    </div>

    <div v-if="contarSenha > 0">

      <p>Sua senha possui {{ contarSenha }} caracteres.</p>

      <div class="senhaForte" v-if="contarSenha > 8">
        <p>Ótimo!</p>
        <p>Sua senha possui mais que 8 caracteres. Sua senha é forte!</p>
      </div>

      <div class="senhaFraca" v-else-if="contarSenha < 5">
        <p>Atenção!</p>
        <p>Sua senha possui menos que 5 caracteres. Sua senha é fraca.</p>
      </div>

      <div class="senhaMedia" v-else="contarSenha">
        <p>Bom.</p>
        <p>Sua senha possui 5 a 8 caracteres. Sua senha possui tamanho médio.</p>
      </div>

    </div>
  </div>
</template>

<style scoped>
.container {
  display: grid;
  place-content: center;
  text-align: center;
  font-family: 'Courier New', Courier, monospace;
}

.container>div {
  background-color: rgb(255, 210, 217);
  min-width: 700px;
}

.inputSenha {
  padding: 10px 0 10px 0;
}

.senhaForte {
  color: white;
  background-color: rgb(197, 99, 115);
  padding: 10px;
  margin: 10px;
  border: 3px solid rgb(161, 65, 81);
  font-weight: bold;
}
.senhaFraca{
  color: white;
  background-color: rgb(242, 161, 174);
  padding: 10px;
  margin: 10px;
  border: 3px solid rgb(233, 127, 144);
  font-weight: bold;
}
.senhaMedia{
  color: white;
  background-color: rgb(223, 123, 140);
  padding: 10px;
  margin: 10px;
  border: 3px solid rgb(198, 86, 105);
  font-weight: bold;
}
</style>
