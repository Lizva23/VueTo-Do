<template>
    <div class="todo-body">
        <h3>To-Do List</h3>
        <div>
            <p>description</p>
            <input type="text" v-model="newTodo.description">
            <p>Date</p>
            <input type="date" v-model="newTodo.date">
            <button @click="toggleAdd">
                <span>Add</span>
            </button>
        </div>
        <div class="checkbox">
            <input type="checkbox">
            <p>view completed tasks</p>
        </div>
        <div class="table-body">
            <table>
                <thead>
                    <tr>
                        <th>Description</th>
                        <th>Date</th>
                        <th>Action</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(task, index) in todo" :key="index">
                        <td>{{ task.description }}</td>
                        <td>{{ task.date }}</td>
                        <td>
                            <div v-show="task.completed == false">
                                <button @click="toggleComplete(index)">complete</button>
                            </div>
                            <div v-show="task.completed == false">
                                <button @click="toggleDelete(index)">delete</button>
                            </div>
                            <div v-if="task.completed">Completed</div>
                        </td>                      
                    </tr>
                </tbody>
            </table>
        </div>     
    </div>
</template>
<script>
    export default{ 
        data(){
            return{
                showComplete: true,
                showDelete: true,
                todo: [],
                newTodo: {
                    description: "",
                    date: "",
                    completed: true
                }
            }
        },
        methods: {
            toggleAdd(){
                    if (this.newTodo.description !== "" && this.newTodo.date !== ""){
                        this.todo.push({
                        date: this.newTodo.date,
                        description: this.newTodo.description,
                        completed: false,
                    });
                    this.newTodo.description = "",
                    this.newTodo.date = ""
                    }
                    
                
                
            },
            toggleComplete(index){
                this.todo[index].completed = true
            },
            toggleDelete(index){
                this.todo.splice(index, 1)
            }
        }
    }
</script>

<style>
.todo-body{
    background-color: aqua;
    width: 400px;
    text-align: center;  
}
.checkbox{
    text-align: start;
    display: flex;
}
table{
    border: 1px solid;
}
table th{
    border: 1px solid;
    padding: 5px;
}
table td{
    border: 1px solid;
    padding: 5px;
}
</style>