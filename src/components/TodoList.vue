<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <p class="display-3">
                    Vue Crash Course
                </p>
            </div>
        </div>
        <div class="row">
            <NewTodo @on-addtodo="addToDo($event)"/>
        </div>
        <div class="row">
            <div class="col-12 col-lg-6">
                <ul class="list-group">
                    <Todo v-for="(todo, index) in todos" :key="index"
                    :todoString="todo.todoString"
                    :completed="todo.completed"
                    @on-delete="deleteToDo(todo)"
                    @on-toggle="toggleToDo(todo)"
                    @on-edit="editToDo(todo, $event)"
                    />
                </ul>
            </div>
        </div>
    </div>
</template>


<script>
import Todo from "./Todo"
import NewTodo from "./NewTodo"
export default {
    components:{
        Todo,
        NewTodo
    },
    data(){
        return{
            todos:[
                {todoString: "Make Angular Course", completed: false},
                {todoString: "Cook some food", completed: true},
                {todoString: "Make Youtube videos", completed: true},
                {todoString: "Publish these videos", completed: false},
            ]
        }
    },
    methods: {
        addToDo(newToDo){
            this.todos.push({
                todoString: newToDo,
                completed: false
            })
        },
        toggleToDo(todo){
            todo.completed = !todo.completed;
        },
        editToDo(todo, newTodoString){
            todo.todoString = newTodoString;
        },
        deleteToDo(deleteTodo){
            this.todos = this.todos.filter(todo => todo !== deleteTodo)
        }
    }
};
</script>


<style>

</style>