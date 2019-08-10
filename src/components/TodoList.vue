<template>
    <div class="container mx-auto px-4 py-20 flex flex-col flex-wrap">
        <h1 class="font-hairline text-6xl text-center text-gray-500">Todo App</h1>
        
            <todo-card class="mx-auto mt-4 h-64 w-full max-w-lg">
            
            <!--input for get a task -->
            <input type="text" class="font-hairline w-full" placeholder="Enter your Task Here" v-model="newTodo" @keyup.enter="addTodo">
            
            <!--for loop to show task in web page-->
            <div v-for="(task, index) in tasks" :key="task.id" class="flex mt-0.75 justify-between">
                <div class="flex items-center"> 
                    <input type="checkbox" v-model="task.completed">
                   <div v-if="!task.editing" @dblclick="editTodo(task)">
                       <div v-if="task.completed" class="">
                           </div> 
                       {{ task.title }}
                   </div>
                   <input v-else type="text" v-model="task.title" class="border-solid border-2 border-gray-600" @blur="doneTask(task)" @keyup.enter="doneTask(task)" v-focus @keyup.esc="cancelEdit(task)">
                </div>                
                <div class="cursor-pointer hover:text-black mt-4 text-gray-500" @click="removeTodo(index)">
                   &times;
                </div>
            </div>
            
        </todo-card>

        <todo-card class="mx-auto mt-10 w-full max-w-lg">
            Create/Edit Task 
        </todo-card>
    </div>
</template>

<script>
export default {
    props: {

    },

    data () {
        return {
            newTodo: '', 
            idForTodo: 3,
            beforeEditCache: '',
            tasks: [
                {
                    id: 1,
                    title: 'Acividad 1 ',
                    done: false,
                    editing: false
                },
                {
                    id: 2,
                    title: 'Example2 task2',
                    done: false,
                    editing: false
                }
            ]
        };
    },

    directives: {
      focus: {

          inserted: function (el) {
              el.focus
          }
      }

    },

    mounted () {

    },

    methods: {
       addTodo(){
           if(this.newTodo.trim().length == 0){
               return
           }

           this.tasks.push({
               id: this.idForTodo,
               title: this.newTodo,
               done: false,
           })
        this.newTodo=''
        this.idForTodo++
    },

    editTodo(task){
       this.beforeEditCache = task.title
       task.editing = true

    },
    doneTask(task){
        task.editing = false
        if(task.title.trim() == ''){
               task.title = this.beforeEditCache
           }
    },

    cancelEdit(task){
         task.title = this.beforeEditCache
         task.editing = false 
    },

       removeTodo(index){
         this.tasks.splice(index, 1)
       }
    }
}
</script>