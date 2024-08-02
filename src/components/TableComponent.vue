<script setup lang="ts">
          
import { defineProps,ref } from "vue";

const props = defineProps<{
  todos: Task[];
}>();

let getProps =ref([]);
 getProps.value = props.todos;

function deleteTodo(todo: Task) {
          getProps.value = getProps.value.filter((t) => t !== todo)
}

</script>
<template>
  <h2>Liste des tâches</h2>
  <div class="list-task">
    <table v-if="todos.length > 0" class="table table-striped table-hover">
      <thead class="table-dark">
        <tr>
          <th>#</th>
          <th>ID</th>
          <th>Tâche</th>
          <th>Etat</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="todo in getProps" :key="todo.id">
          <td>
            <input type="checkbox" v-model="todo.state" />
          </td>
          <td>{{ todo.id }}</td>
          <td :class="{ state: todo.state }">{{ todo.text }}</td>
          <td>{{ todo.state ? "Traité" : "Non traité" }}</td>
          <td>
            <button class="btn btn-success mx-3" @click="updateTodo()">
              Modifier
            </button>
            <button class="btn btn-danger" @click="deleteTodo(todo)">
              Supprimer
            </button>
          </td>
        </tr>
      </tbody>
    </table>
    <p v-else>Chargement en cours</p>
  </div>
</template>

<style></style>
