<template>
    <div>
        <input v-model="newText" type="text">
        <button @click="addTask">Добавить</button>

            <ul>
                <li v-for="task in tasks" :key="task.id" :style="{ 'text-decoration': task.isEdit ? 'line-through' : 'none' }">
                

                <template v-if="task.isEdit2 == true">
                <input type="text" v-model="task.text   ">    
                <button @click="editTask(task)">Сохранить</button>
                <button @click="deleteAff(task.id)">Удалить</button>
                </template>

                <template v-else>
                {{ task.text }}
                <input type="checkbox" v-model="task.isEdit">
                <button @click="editTask(task) ">Изменить</button>
                <button @click="deleteAff(task.id)">Удалить</button>
                </template>
                </li>
            </ul>

    </div>
</template>
<script>
export default {
    name: 'Check',
    props:{
        tasks: Object,
        newText: String,
    },
    emits:['addTask', 'deleteTask', 'editTask'],

    data(){
        return{
            newText: '',
        }
    },
    methods:{
        deleteAff(id){
            this.$emit('deleteTask', id)
        },
        addTask(){
            this.$emit('addTask', this.newText)
        },
        editTask(task){
            this.$emit('editTask', task)
        },
    },
    
}
</script>
<style>

</style>