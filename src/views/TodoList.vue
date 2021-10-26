<template>
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
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

interface Todo {
  id: number;
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
}
</script>
