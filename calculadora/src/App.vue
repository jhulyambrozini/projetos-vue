 
<template>
  <main>
    <h1>Calculadora Aritmética</h1>

    <div class="calculadora">
      <input type="number" placeholder="digite um número" v-model="num1" @change="calcular">
      <input type="number" placeholder="digite um número" v-model="num2" @change="calcular">
      <select v-model="operacao" @change="calcular">
        <option value="+">Adição</option>
        <option value="-">Subtração</option>
        <option value="/">Divisão</option>
        <option value="*">Multiplicação</option>
      </select>
    </div>

    <div class="resultado">
      <p>O resultado da operação é: </p>
      <input v-model="resultado" disabled>
    </div>
  </main>
</template>

<script>

export default {
  data() {
    return {
      num1: 0,
      num2: 0,
      operacao: '',
      resultado: 0
    }
  },

  methods: {
    calcular() {
      switch (this.operacao) {
        case '+':
          this.resultado = parseFloat(this.num1) + parseFloat(this.num2);
          break;
        case '-':
          this.resultado = parseFloat(this.num1) - parseFloat(this.num2);
          break;
        case '*':
          this.resultado = parseFloat(this.num1) * parseFloat(this.num2);
          break;
        case '/':
          this.resultado = parseFloat(this.num1) / parseFloat(this.num2);
          break;
        default:
          this.resultado = 0;
      }
    }
  }
}

</script>

<style scoped>
main {
  margin: 0 auto;
  padding-bottom: 24px;
  height: auto;
  width: 700px;
  background-color: rgb(50, 120, 164);
  color: #fff;
  border-radius: 4px;
  text-align: center;
  font-family: Arial, Helvetica, sans-serif;
}

h1 {
  padding-top: 100px;
}

.calculadora {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin: 24px 0;
}

.calculadora input,
.calculadora select {
  border-radius: 5px;
  outline: none;
  border: none;
  padding: 10px;
}

.resultado {
  font-size: 20px;
}

.resultado input {
  background-color: transparent;
  color: #fff;
  border: 1px solid #fff;
  border-radius: 5px;
  text-align: center;
  padding: 8px;
}

@media (max-width: 426px) {

  main {
    width: 400px;
  }

  h1 {
    padding-top: 50px;
  }
  .calculadora {
    display: grid;
  }
}
</style>
