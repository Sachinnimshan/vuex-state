<template>
    <div>
        <h3>ToDoS</h3>
        <div class="legend">
            <span>Double Click To Mark As Complete</span>
            <div class="completed">Completed</div>
            <div class="not-completed">Not Completed</div>
        </div>
        <div class="todos">
            <div @dblclick="onDblClick(todo)" 
            v-for="todo in allTodos" 
            :key="todo.id" 
            class="todo"
            v-bind:class="{'is-completed': todo.completed}">
                {{todo.title}}
                <div class="delete-icon"><i @click="deleteTodo(todo.id)" class="fas fa-trash-alt"></i></div>
            </div>
        </div>
    </div>
</template>

<script>
import {mapGetters, mapActions} from 'vuex';
export default {
    name: "Todos",
    methods: {
        ...mapActions(['fetchTodos','deleteTodo', "updateTodo"]),
        onDblClick(todo){
            const updTodo ={
                id: todo.id,
                title: todo.title,
                completed: !todo.completed
            }
            this.updateTodo(updTodo);

        }
    },
    computed: mapGetters(['allTodos']),
    created(){
        this.fetchTodos();
    }
    
    
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

.legend{
    display: flex;
    align-items: center;
    gap: 1rem;
    text-align: center;
    margin: 1rem;
    font-family: 'Roboto', sans-serif;
    font-weight: 600;
    letter-spacing: 1px;
    flex-wrap: wrap;
}

.is-complete{
    background: greenyellow;
}

.completed{
    background: greenyellow;
    width: 140px;
    height: 2rem;
    border-radius: 5px;
    border: 1px solid gray;
}

.not-completed{
    background: #E8FCF1;
    width: 140px;
    height: 2rem;
    border-radius: 5px;
    border: 1px solid gray;
}

h3{
    font-family: "Roboto";
    letter-spacing: 1px;
}
.todos{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 2rem;
}

.todo{
    background: #E8FCF1;
    padding: 1rem;
    border: 1px solid #15A04E;
    color: #15A04E;
    font-family: 'Roboto', sans-serif;
    border-radius: 5px;
    text-align: center;
    position: relative;
    cursor: pointer ;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}

.todo:hover{
    transform: scale(1.1);
    transition: transform 0.2s ease-in-out;
}

.delete-icon{
    
    position: absolute;
    right: 10px;
    bottom: 10px;
    cursor: pointer;
}

</style>