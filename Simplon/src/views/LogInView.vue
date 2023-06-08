<template>
    <div class="login-container">
      <h1>Connexion</h1>
      <form @submit.prevent="login">
        <div class="form-group">
          <label for="email">Email:</label>
          <input type="email" id="email" v-model="email" required>
        </div>
        <div class="form-group">
          <label for="password">Mot de passe:</label>
          <input type="password" id="password" v-model="password" required>
        </div>
        <button type="submit">Se connecter</button>
      </form>
    </div>
  </template>
  
  <script>
  import utilisateurs from '../../donnees.json';
  
  export default {
    data() {
      return {
        email: '',
        password: '',
      };
    },
    methods: {
      login() {
        // Vérification des informations de connexion
        const utilisateur = utilisateurs.find(
          (user) => user.email === this.email && user.motDePasse === this.password
        );
  
        if (utilisateur) {
          // Connexion réussie
          console.log('Connexion réussie !', utilisateur);
          // Rediriger vers une autre page ou effectuer d'autres actions
        } else {
          // Informations de connexion invalides
          console.log('Informations de connexion invalides !');
          // Afficher un message d'erreur ou effectuer d'autres actions
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .login-container {
    max-width: 400px;
    margin: 0 auto;
    padding: 40px;
    background-color: #f5f5f5;
    border: 1px solid #ddd;
  }
  
  h1 {
    text-align: center;
    margin-bottom: 20px;
  }
  
  .form-group {
    margin-bottom: 20px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
  }
  
  input {
    width: 100%;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
  }
  
  button {
    display: block;
    width: 100%;
    padding: 10px;
    background-color: #337ab7;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #23527c;
  }
  </style>
  