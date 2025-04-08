<template>
    <div class="container">
        <section class="add-new-task">
            <button @click="newTask">&plus;</button>
        </section>
        <section class="tasks">
            <button class="task" v-for="(task, index) in tasksList" :key="index"
            @click="deleteTask(index)">
                {{ task }}
            </button>
        </section>
    </div>
</template>

<script>
    export default {
        name: 'SimpleTaskList',
        data() {
            return {
                tasksList: ['test']
            }
        },
        methods: {
            newTask() {
                const newTask = prompt('Enter the New Task:')
                if (newTask) {
                this.tasksList.push(newTask)
                }
            },
            deleteTask(i){
                this.tasksList.splice(i, 1)
            }
        }
    }

</script>

<style scoped>
.container {
    margin-top: 50px;
    align-items: center;
    justify-items: center;
}

.tasks {
    display: flex;
    flex-direction: column;
}

.tasks button{
    background-color: rgba(0, 0, 0, 0.4);
    color: white;
    border-radius: 0px;
    border-left: 5px solid darkslateblue;
}

.tasks button:hover {
    text-decoration: line-through;
}
</style>