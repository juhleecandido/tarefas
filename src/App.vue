<template>
<section>
  <cabecalho />

  <div class="container">
    <h2>{{ titulo }}</h2>
    <div class="input-group">
      <input @keyup.enter="adicionarTarefas" v-model="novaTarefa" type="text" />
      <span class="input-group-btn">
        <button @click="adicionarTarefas" class="btn btn-primary">Adicionar Tarefa</button>
      </span>
    </div>
    <ul>
      <li v-for="(tarefa, index) in tarefas" 
      :key="index" 
      :class="{ 'remove': tarefa.checked }"
      >
        <input type="checkbox" v-model="tarefa.checked" />
        <label>{{ tarefa.titulo }}</label>

      </li>
    </ul>
    <footer2>
      <em> Que dia é hoje? </em>
      <input v-model="titulo" type="text"/>
    </footer2>
  </div>
  <rodape />
  </section>
</template>

<script>
import Cabecalho from "@/components/Cabecalho";
import Rodape from "@/components/Rodape";
export default {
  name: "App",
  components: { Cabecalho, Rodape },
  data() {
  
    return {
      titulo: "Segunda-feira", 
      novaTarefa: '',
      tarefas: [
        { titulo: "Estudar", checked: false },
        { titulo: "Leitura", checked: true },
        { titulo: "Caminhada", checked: false },
        { titulo: "Meditação", checked: false },
        { titulo: "Esporte", checked: true },
        { titulo: "Mercado", checked: false },
        { titulo: "Dormir", checked: false },
        { titulo: "Tirar o Lixo", checked: false },
        { titulo: "Programar", checked: false },
        ]
      };
    },
    methods:{
      adicionarTarefas() {
        this.tarefas.push({
          titulo: this.novaTarefa,
          checked: false
        });
        this.novaTarefa = "";
    
      },
    },    
  };

</script>

<style>
section{
  background-color: rgb(202, 202, 233);
}
.container {
  width: 40%;
  margin:20px auto 0px auto;
  
  }

  ul li {
    list-style: none;
  }
  .removed {
    color:gray;
  }

  .removed label {
    text-decoration: line-through;
  }

  
</style>