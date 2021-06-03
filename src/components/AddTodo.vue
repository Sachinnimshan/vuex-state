<template>
    <div class="container">
        <h3>Add New +</h3>
        <div class="add">
            <form @submit="onsubmit">
                <input type="text" v-model="title" placeholder="Add To Do">
                <input type="submit" value="Submit">
            </form>
        </div>
    </div>
</template>

<script>
import {mapActions} from 'vuex';
export default {
    name: "AddTodo",
    data(){
        return{
            title:""
        }
    },
    methods:{
        ...mapActions(["addTodo"]),
        onsubmit(e){
            e.preventDefault();
            this.addTodo(this.title);
        }
    }
    
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
h3{
    font-family: "Roboto";
}
form{
    display: flex;
}

input[type='text']{
    flex: 10;
    padding: 10px;
    background: #E8FCF1;
    border: 2px solid #13A650;
    outline: 0;
    height: 2rem;
    font-size: 18px;
    border-radius: 0.5rem 0 0 0.5rem;
}

input[type='submit']{
    flex: 1.75;
    background: #13A650;
    color: #fff;
    border: 1px solid #13A650;
    cursor: pointer;
    font-size: 18px;
}

</style>