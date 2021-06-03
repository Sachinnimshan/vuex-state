<template>
    <div class="filter-todos">
        Filter
        <select @change="filterTodos($event)" class="select-box">
            <option value="">200</option>
            <option value="">100</option>
            <option value="">50</option>
            <option value="">25</option>
            <option value="">10</option>
        </select>
    </div>
</template>


<script>
import {mapActions} from 'vuex';
export default {
    name: "FilterTodos",
    methods: mapActions(['filterTodos'])
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
.filter-todos{
    margin-top: 1rem;
    font-family: 'Roboto';
    font-size: 18px;
    font-weight: 500;
}

.select-box{
    width: 4rem;
    height: 1.75rem;
    font-size: 16px;
    cursor: pointer;
    border-radius: 5px;
    background: #E8FCF1;
}

</style>