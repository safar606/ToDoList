<script>
export default {
    data() {
        return {
            newTodo: '',
            todos: []
        }
    },
    methods: {
        addTodo() {
            if (!this.newTodo) return
            this.todos.unshift(this.newTodo)
            this.newTodo = ''
        },
        removeTodo(index) {
            this.todos.splice(index, 1)
        }
    }
}
</script>
<template>
    <div class="h-screen bg-blue-600 flex items-center justify-center">
        <div class="container bg-white rounded-lg min-w-[450px] min-h-[100px] w-2/5 p-6 shadow-lg">
            <div id="newtask">
                <input
                    type="text"
                    v-model="newTodo"
                    placeholder="New task ..."
                    class="w-[84%] h-12 px-4 mb-10 text-gray-800 font-medium rounded-md border-2 border-gray-300 focus:outline-none focus:border-blue-500"
                />
                <button
                    @click="addTodo"
                    class="float-right w-[15%] h-12 font-medium text-white bg-blue-700 rounded-md focus:outline-none hover:bg-blue-800">
                    Add
                </button>
            </div>
            <div id="tasks">
                <ul>
                    <li
                        v-for="(todo, index) in todos"
                        :key="index"
                        class="task flex items-center justify-between bg-blue-200 rounded-md border border-gray-400 p-2 mb-3 cursor-pointer">
                        {{ todo }}
                        <button
                            @click="removeTodo(index)"
                            class="m-1 w-12 h-full rounded-md">
                            <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M7 21C6.45 21 5.97933 20.8043 5.588 20.413C5.19667 20.0217 5.00067 19.5507 5 19V6H4V4H9V3H15V4H20V6H19V19C19 19.55 18.8043 20.021 18.413 20.413C18.0217 20.805 17.5507 21.0007 17 21H7ZM17 6H7V19H17V6ZM9 17H11V8H9V17ZM13 17H15V8H13V17Z" fill="black"/>
                            </svg>
                        </button>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<style>
</style>

