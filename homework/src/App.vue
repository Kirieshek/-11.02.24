<template>
  <Check :tasks="tasks"  @addTask="addTask" @deleteTask="deleteTask" @editTask="editTask"/>
</template>

<script>
import Check from './components/Check.vue'

export default {
  name: 'App',
  components:{
    Check
  },
data(){
  return{
    tasks:[
      {id: 1, text: 'Помыться', isEdit: false, isEdit2: false,},
      {id: 2, text: 'Покушать', isEdit: false, isEdit2: false,},
      {id: 3, text: 'Убраться', isEdit: false, isEdit2: false,},
      {id: 4, text: 'Прогуляться', isEdit: false, isEdit2: false,},
      {id: 5, text: 'Поваляться', isEdit: false, isEdit2: false,},
    ],
   }
}
,
methods:{
      addTask(newText){
        this.tasks.unshift({
          id: Date.now(),
          text: newText,
          isEdit2: false,
        })
      },
      deleteTask(id) {
      this.tasks = this.tasks.filter(tasks => tasks.id !== id)
      },
      editTask(task) {
      task.isEdit2 = !task.isEdit2
    },
    },
  }


</script>

<style>

</style>
