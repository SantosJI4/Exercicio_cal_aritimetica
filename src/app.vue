<script setup>
  import {ref, computed} from 'vue';
  const num1 = ref(0);
  const num2 = ref(0);
  const operador = ref('+')

  const resultado = computed(() => {
    switch (operador.value) {
      case '+':
        return parseFloat(num1.value) + parseFloat(num2.value);
      case '-':
          return parseFloat(num1.value) - parseFloat(num2.value);
      case '*':
          return parseFloat(num1.value) * parseFloat(num2.value);
      case '/':
          return num1.value != 0 ? parseFloat(num1.value) / parseFloat(num2.value) : 'Erro: Divisão por zero';
        default:
          return "operador invalido."
        }
  })
</script>

  <template>
    <div class="container">
      <div>
        <h1>
        Calculadora Aritmética EBAC ;)
        </h1>
    </div>
    <div>
      <label for="num1">Número 1:</label>
      <input id="num1" type="number" v-model="num1" @keyup="calculo" />
    </div>
    <div>
      <label for="operador">Operador:</label>
      <select id="operador" v-model="operador" @change="calculo">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
    </div>
      <div>
        <label for="num2">Número 2:</label>
        <input type="number" id="num2" v-model="num2" @keyup="calculo"/>
      </div>
      <div>
        <label for="resultado">Resultado:</label>
        <input type="text" id="resultado" :value="resultado" readonly/>
      </div>
    </div>
  </template>
  <style scoped>
    .container {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100dvh;
      font-family: Arial, sans-serif;
    }
    h1 {
      color: #4CAF50;
    }
    label {
      margin-right: 10px;
    }
    input[type="text"] {
      background-color: #f0f0f0;
      border: 1px solid #ccc;
      padding: 5px;
      margin: 10px;
      width: 200px;
    }
    input[type="number"] {
      width: 100px;
      margin: 10px;
      border-radius: 3px;
    }
    select {
      width: 50px;
    }
</style>