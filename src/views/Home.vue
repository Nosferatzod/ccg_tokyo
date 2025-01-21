<template>
  <div class="home">
    <AppHeader />
    <MainContent />
    <UserForm @submitUser="addUser" />

    <!-- Seção de Cartões de Identificação -->
    <div class="card-container">
      <div class="card left-card">
        <img 
          src="../assets/images/arima.jpg" 
          alt="Cartão 1" 
          @click="openModal('../assets/images/arima.jpg')" 
          class="zoom-image"
        />
      </div>
      <div class="card right-card">
        <img 
          src="../assets/images/haise.png" 
          alt="Cartão 2" 
          @click="openModal('../assets/images/haise.png')" 
          class="zoom-image"
        />
      </div>
    </div>

    <div class="card-container-bottom">
      <div class="card-item">
        <img 
          src="../assets/images/suzuya.jpg" 
          alt="Cartão 3" 
          @click="openModal('../assets/images/suzuya.jpg')" 
          class="zoom-image"
        />
      </div>
      <div class="card-item">
        <img 
          src="../assets/images/nagai.jpg" 
          alt="Cartão 4" 
          @click="openModal('../assets/images/nagai.jpg')" 
          class="zoom-image"
        />
      </div>
    </div>

    <!-- Modal para visualizar a imagem em tamanho maior -->
    <div v-if="isModalOpen" class="modal" @click="closeModal">
      <div class="modal-content">
        <img :src="modalImage" alt="Imagem ampliada" class="modal-image" />
      </div>
    </div>

    <!-- Tabela de usuários cadastrados -->
    <div v-if="users.length > 0" class="user-table-container">
      <h2>Usuários Cadastrados</h2>
      <table class="user-table">
        <thead>
          <tr>
            <th>Nome</th>
            <th>Email</th>
            <th>CPF</th>
            <th>Telefone</th>
            <th>Data de Nascimento</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(user, index) in users" :key="index">
            <td>{{ user.name }}</td>
            <td>{{ user.email }}</td>
            <td>{{ user.cpf }}</td>
            <td>{{ user.phone }}</td>
            <td>{{ user.birthDate }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import AppHeader from '../components/Header.vue';
import MainContent from '../components/MainContent.vue';
import UserForm from '../components/UserForm.vue';  // Corrigido para UserForm

export default {
  name: 'UserHome',
  components: {
    AppHeader,
    MainContent,
    UserForm  // Corrigido para UserForm
  },
  data() {
    return {
      isModalOpen: false,  // Controla a exibição do modal
      modalImage: '',       // Armazena a imagem selecionada para exibição no modal
      users: []            // Armazena os usuários cadastrados
    };
  },
  methods: {
    openModal(imageSrc) {
      this.modalImage = imageSrc;  // Definir o caminho da imagem para o modal
      this.isModalOpen = true;     // Abrir o modal
    },
    closeModal() {
      this.isModalOpen = false;    // Fechar o modal
      this.modalImage = '';        // Limpar a imagem do modal
    },
    addUser(userData) {
      // Adiciona o usuário ao array de usuários
      this.users.push(userData);
    }
  }
}
</script>

<style scoped>
.home {
  font-family: 'Arial', sans-serif;
  background-color: #222;
  color: #fff;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.card-container {
  display: flex;
  justify-content: center;  /* Centraliza os cartões no eixo horizontal */
  align-items: center;      /* Alinha verticalmente no centro */
  gap: 20px;
  margin-top: 20px;
  margin-bottom: 20px;  /* Adiciona um espaço entre os cartões e a parte inferior */
}

.card {
  width: 200px;
  height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #444;
  border-radius: 10px;
}

.left-card, .right-card {
  width: 200px;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #444;
  border-radius: 10px;
}

.left-card img, .right-card img {
  width: 100%;
  height: auto;
  border-radius: 10px;
}

.card-container-bottom {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-top: 20px;
}

.card-item {
  width: 200px;
  height: 100px;
  background-color: #444;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 10px;
}

.card-item img {
  width: 100%;
  height: auto;
  border-radius: 10px;
}

.zoom-image {
  transition: transform 0.3s ease;  /* Efeito de zoom */
}

.zoom-image:hover {
  transform: scale(1.1);  /* Aumenta a imagem quando passa o mouse */
}

.modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 999;
}

.modal-content {
  position: relative;
}

.modal-image {
  max-width: 80%;
  max-height: 80%;
  border-radius: 10px;
}

/* Estilos da tabela de usuários */
.user-table-container {
  margin-top: 40px;
  width: 80%;
  background-color: #333;
  padding: 20px;
  border-radius: 10px;
}

.user-table {
  width: 100%;
  border-collapse: collapse;
}

.user-table th, .user-table td {
  padding: 10px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

.user-table th {
  background-color: #444;
}

.user-table td {
  background-color: #555;
}
</style>
