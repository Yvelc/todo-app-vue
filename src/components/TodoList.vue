<template>
    <div class="container mx-auto px-4 py-20 flex flex-col flex-wrap">
        <h1 class="font-hairline text-6xl text-center text-blue-300 ">Todo App R&Y </h1>

        <todo-card class="mx-auto mt-4 h-64 w-full max-w-lg">
            Todo List Ruben e Yvelc
        </todo-card>

        <todo-card class="mx-auto mt-10 w-full max-w-lg">
            Create/Edit/Eliminate Task
        </todo-card>
    </div>
</template>

<script>
export default {
    props: {

    },

    data () {
        return {
            tasks: [
                {
                    id: 1,
                    title: 'Example task',
                    done: false
                }
            ]
        };
    },

    mounted () {

    },

    methods: {

    }
}
</script>