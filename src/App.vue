<script setup lang="ts">
  import { ref} from 'vue';
import FormComponentVue from "./components/FormComponent.vue";
import TableComponentVue from "./components/TableComponent.vue";

let id: number = 1;
interface Task {
          id: number,
          text: string,
          state: boolean
}
const todos = ref<(Task[])>([]);

function addTodo(taskname:string) {
          todos.value.push({ id: id++, text: taskname, state: false });
}


</script>

<template>
  <main>
    <div class="container">
      <FormComponentVue @emitName="addTodo" />
      <TableComponentVue :todos="todos" />
    </div>
  </main>
</template>

<style scoped></style>
