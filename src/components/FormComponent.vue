<script setup lang="ts">
import { ref } from 'vue';

const emit = defineEmits<{
emitName: [value: string]
}>()


const newTodo = ref<string>('');

function createTask():void {
          emit("emitName",newTodo.value);
          newTodo.value = '';
}

// function updateTodo() {
//           todos.value = todos.value.findIndex((t: string) => t.todo === todo.todo);

// }


</script>
<template>
         <h1>Todo List avec Vue JS et Typescript</h1>
      <div class="form card">
        <form @submit.prevent="createTask">
          <div class="form">
            <div>
              <input
                v-model="newTodo"
                type="text"
                class="input form-control"
                required
              />
            </div>
            <div><button class="btn btn-primary addbtn">Ajouter</button></div>
          </div>
        </form>
      </div>
</template>


<style scoped>
.container {
          text-align: center;
          margin-top: 2rem;
}

.form {
          display: flex;
          justify-content: space-around;
          align-items: center;
}


.input {
          padding: 1rem;
          margin: 2rem auto;
          border: none;
          border-radius: 0.5rem;
          font-size: 1.5rem;
          width: 500px;
          background-color: #262626;
          border-style: none;
          color: #fff;
}

.addbtn {
          padding: 1rem;
          font-size: 1.4rem;
          margin-left: 20px;
          background-color: #4ea8de;
          border-radius: 0.5rem;
          border: none;
          color: #fff;
}

h2 {
          text-decoration: underline;
}
.state {
          text-decoration: line-through;
          color: #ee0a0a;

}


</style>