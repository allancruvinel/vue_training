<template>
  <div class="" id="app">
    <div class="container grid-xs py-2">
      <img
        class="img-responsive img-logo"
        src="@/assets/logo.png"
        alt="logomarca"
      />
      <form @submit.prevent="addTodo(todo)"> <!-- cria um form passando o objeto todo como parametro para a função, com o reload da pagina desativado -->
        <div class="input-group">
          <input
            type="text"
            v-model="todo.frase" 
            class="form-input"
            placeholder="Novo todo"
          /> <!-- v-model espera o valor dentro do unput com a variavel da função reativa Data() -->
          <button class="btn btn-primary input-group-btn">Adicionar</button>
        </div>
      </form>
      <div class="todo-list">
        <Todo v-for="t in todos" :key="t.id" @toogle="toogleTodo" :todo="t"/> <!--  -->
      </div>
    </div>
  </div>
</template>

<script>
import Todo from './components/Todo'

export default {
  name: "App",
  components: {Todo}, //traz o componente template para realizar o for de itens
  data() {
    return { todos: [], todo: { checked : false } }; // seta as variáveis de evento que serão alteradas instantâneamente
  },
  methods: {
    addTodo() {
      this.todo.id = Date.now();
      this.todos.push(this.todo);
      this.todo = { checked : false};
    },

    toogleTodo(todo) {
      const index = this.todos.findIndex(item => item.id === todo.id)
      if (index > -1){
        const checked = !this.todos[index].checked
        this.$set(this.todos,index,{...this.todos[index],checked});
      }
    }
  }
}; //https://youtu.be/rcDm0UBfXpM?t=510 Continuar a Aula, https://youtu.be/cSa-SMVMGsE?t=965 (aula opcional)
</script>

<style scoped>
.img-logo {
  max-width: 200px;
  margin: 0 auto;
}
.todo-list {
  padding-top: 1rem;
}
</style>
