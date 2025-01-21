<template>
  <form @submit.prevent="submitForm">
    <div class="form-group">
      <label for="name">Nome:</label>
      <input
        type="text"
        id="name"
        v-model="name"
        @input="toUpperCase"
        required
      />
    </div>
    <div class="form-group">
      <label for="email">Email:</label>
      <input type="email" id="email" v-model="email" required />
    </div>
    <div class="form-group">
      <label for="cpf">CPF:</label>
      <input type="number" id="cpf" v-model="cpf" required />
    </div>
    <div class="form-group">
      <label for="phone">Telefone:</label>
      <input type="number" id="phone" v-model="phone" required />
    </div>
    <div class="form-group">
      <label for="birthDate">Data de Nascimento:</label>
      <input type="date" id="birthDate" v-model="birthDate" required />
    </div>
    <button type="submit">Cadastrar</button>
  </form>
</template>

<script>
import { VueTheMask } from 'vue-the-mask';

export default {
  directives: {
    mask: VueTheMask
  },
  data() {
    return {
      name: '',
      email: '',
      cpf: '',
      phone: '',
      birthDate: ''
    };
  },
  methods: {
    toUpperCase() {
      this.name = this.name.toUpperCase();
    },
    submitForm() {
      const userData = {
        name: this.name,
        email: this.email,
        cpf: this.cpf,
        phone: this.phone,
        birthDate: this.birthDate
      };

      // Emite os dados para o componente pai (Home.vue)
      this.$emit('submitUser', userData);

      // Limpar o formulário após o envio
      this.name = '';
      this.email = '';
      this.cpf = '';
      this.phone = '';
      this.birthDate = '';
    }
  }
}
</script>


<style scoped>
.form-container {
  background-color: #444;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.7);
  text-align: center;
}

.form-container h3 {
  color: #fff;
  font-size: 1.8rem;
  margin-bottom: 20px;
}

.form-group {
  margin: 10px 0;
}

input {
  padding: 10px;
  border: 1px solid #666;
  border-radius: 5px;
  width: 80%;
  background-color: #222;
  color: #fff;
}

button {
  background-color: #ff5c5c;
  color: #fff;
  border: none;
  padding: 10px 20px;
  font-size: 1.1rem;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #e04e4e;
}
</style>
