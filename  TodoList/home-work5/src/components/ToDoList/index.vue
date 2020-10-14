<template>
    <div>
        <h1>Lets reach the Goals</h1>
        <div>
            <label> search for goals</label>
            <input type="text" v-model="searchGoal">
        </div>
        <div>
            <label> What is next goal?</label>
            <input type="text" v-model="myTask">
            <button @click="addTask">add new task</button>
        </div>
        <div>

            <to-do-item v-for="taskItem in filterGoal" :key="taskItem.id"
                :task="taskItem.task"
                :time="taskItem.time"
                :status='taskItem.status'
                
                @postponed="onPostponed(taskItem.id)"
                @done="onDone(taskItem.id)"
                @plan="onPlan(taskItem.id)"
                
                
             />
        </div>
    </div>
</template>

<script>
import ToDoItem from "./ToDoItem";
import uniqid from "uniqid";

    export default {
        name:"ToDoList",

        components: {
            ToDoItem,
        },

        props: {
            taskList: {
                type: Array,
                default: ()=>[]
            },
            
        },

        data() {
            return {
                myTask: null,
                searchGoal: null
                
                
            }
        },
        computed: {
        filterGoal() {
                if(!this.searchGoal) return this.taskList //Автоматичо викликається сеттер (метод get)
                else
                {const text=this.searchGoal.toLowerCase()
                    return this.taskList.filter(item=>item.task.toLowerCase().includes(text)) }
            },
        },

        watch: {
            searchGoal(newValue, oldValue) {
                console.log(`${newValue} -  ${oldValue}`);
                
            }
        },

        methods: {

            addTask (){
                const time=new Date()
               const newTaskOb={   
                        id:uniqid(),                 
                        task:this.myTask,
                        time:` ${time.getHours()}.${time.getMinutes()} .${time.toLocaleDateString()} `,
                        status:"NEW"  
                                        
                }
                console.log(uniqid());

                this.taskList=[...this.taskList,newTaskOb]
            },

            onPostponed(id) {
                const task=this.taskList.find(item=>item.id===id)
                task.status='POSTPONED'
            },

           
            onPlan(id) {
                const task=this.taskList.find(item=>item.id===id)
                task.status='PLAN'

            },
             onDone(id) {
                const task=this.taskList.find(item=>item.id===id)
                task.status='DONE'

            }


        },
    }
</script>

<style lang="scss" scoped>

</style>