<template>
 <div>
  <form @submit.prevent="salvar">
    <label for="nome">Nome</label>
    <input type="text" id="nome" v-model="nome" size="20"><br>
    <label for="nota1">Nota 1</label>
    <input type="number" id="nota1" v-model="nota1"><br>
    <label for="nota2">Nota 2</label>
    <input type="number" id="nota2" v-model="nota2"><br>
    <label for="nota3">Nota 3</label>
    <input type="number" id="nota3" v-model="nota3"><br>
    <input type="submit" :value="salvarNota">
    <br>
  </form>

  <table class="table" border="1">
            <tr>
              <th>Nome</th>
              <th>Nota1</th>
              <th>Nota2</th>
              <th>Nota3</th>
              <th>Media</th>
              <th>Situação</th>
            </tr>
            <tr v-for="n in notas" :key="n.nome">
                <td>{{ n.nome }}</td>
                <td>{{ n.nota1 }}</td>
                <td>{{ n.nota2 }}</td>
                <td>{{ n.nota3 }}</td>
                <td>{{n.media}}</td>
                <td>{{n.situacao}}</td>
            </tr>
            
          </table>
 </div>
  
  </template>

<script>
/*import CalculaNota from './components/CalculaNota.vue';*/

export default {
  components: {
    /*CalculaNota*/
},
data() {
  return {
    notas: [
      {
        nome: "Ricardo",
        nota1: 5,
        nota2: 10,
        nota3: 5,
        media: 7,
        situacao: "Aprovado"
      }
    ],
    nome: "",
    nota1: null,
    nota2: null,
    nota3: null,
    media: null,
    situacao: ""
  }
},

methods: {
  inserir() {
      this.notas.push(
        {
          nome: this.nome,
          nota1: this.nota1,
          nota2: this.nota2,
          nota3: this.nota3,
          media: (this.nota1 + this.nota2*2 + this.nota3*3)/6
        }
      )

      return true
    },

  salvar() {
  this.inserir();
  
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
