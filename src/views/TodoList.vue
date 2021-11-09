<template>
  <section>
    <v-card class="ma-2">
      <v-toolbar color="purple" dark>
        <v-toolbar-title>Todo List</v-toolbar-title>
      </v-toolbar>

      <v-simple-table>
        <template v-slot:default>
          <thead>
            <tr>
              <th class="text-left">Title</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="todo in todos" :key="todo.id">
              <td>{{ todo.title }}</td>
            </tr>
          </tbody>
        </template>
      </v-simple-table>
    </v-card>

    <v-card class="ma-2">
      <v-toolbar color="purple" dark>
        <v-toolbar-title>New Todo</v-toolbar-title>
      </v-toolbar>

      <v-form class="pa-2">
        <v-text-field
          v-model="newTodo.title"
          label="Title"
          hide-details="auto"
        />

        <v-text-field
          v-model="newTodo.description"
          label="Description"
          hide-details="auto"
        />

        <v-btn class="mt-1" color="success" @click="post">Post</v-btn>
      </v-form>
    </v-card>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

interface Todo {
  id: number;
  title: string;
  description: string;
}

interface NewTodo {
  title: string;
  description: string;
}

@Component
export default class TodoList extends Vue {
  todos: Todo[] = [
    {
      id: 1,
      title: "ToDoリスト画面を実装",
      description: "ToDoリスト画面を作成する。\nタイトルを表示する。",
    },
    {
      id: 2,
      title: "新規ToDo画面を実装",
      description:
        "新規ToDo画面を作成する。タイトルと説明を登録する。登録したらToDoリストを表示する。ToDoリスト画面から新規ToDo画面を表示する",
    },
    {
      id: 3,
      title: "ToDoリスト画面とWEB APIを連携",
      description: "WEB APIからToDoリストを取得して表示する。",
    },
    {
      id: 4,
      title: "新規ToDo画面とWEB APIを連携",
      description: "WEB APIにToDoリストを登録する。",
    },
    {
      id: 5,
      title: "ToDoの削除機能を実装",
      description: "WEB APIでToDoを削除する。",
    },
  ];

  newTodo: NewTodo = {
    title: "",
    description: "",
  };

  post(): void {
    this.todos.push({
      id: this.todos.length,
      title: this.newTodo.title,
      description: this.newTodo.description,
    });

    this.newTodo.title = "";
    this.newTodo.description = "";
  }
}
</script>
