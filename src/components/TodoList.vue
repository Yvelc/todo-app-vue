<template>
    <div class="container mx-auto px-4 py-20 flex flex-col flex-wrap">
        <h1 class="font-hairline text-6xl text-center text-blue-500">Todo App R&Y</h1>
       
            <todo-card class="mx-auto mt-4 h-64 w-full max-w-lg">
            
            <!--input for get a task -->
            <input type="text" class="font-hairline w-full" placeholder="Enter your Task Here" v-model="newTodo" @keyup.enter="addTodo">
            
            <!--for loop to show task in web page-->
            <div v-for="(task, index) in tasks" :key="task.id" class="flex mt-0.75 justify-between">
                <div> 
                    {{ task.title }} 
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
            tasks: [
                {
                    id: 1,
                    title: 'Acividad 1 ',
                    done: false
                },
                {
                    id: 2,
                    title: 'Example2 task2',
                    done: false
                }
            ]
        };
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

       removeTodo(index){
         this.tasks.splice(index, 1)
       }
    }
}
</script>