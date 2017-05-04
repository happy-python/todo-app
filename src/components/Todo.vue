<template>
    <div class='ui centered card'>
        <!--Todo shown when we are not in editing mode.-->
        <div class="content" v-show="!isEditing">
            <div class='header'>
                {{ todo.title }}
            </div>
            <div class='meta'>
                {{ todo.project }}
            </div>
            <div class='extra content'>
                <span class='right floated edit icon' @click="isEditing=true">
                    <i class='edit link icon'></i>
                </span>
                <span class='right floated trash icon' @click="deleteTodo(todo)">
                    <i class='trash link icon'></i>
                </span>
            </div>
        </div>
        <!--form is visible when we are in editing mode-->
        <div class="content" v-show="isEditing">
            <div class='ui form'>
                <div class='field'>
                    <label>Title</label>
                    <input type='text' v-model="todo.title">
                </div>
                <div class='field'>
                    <label>Project</label>
                    <input type='text' v-model="todo.project">
                </div>
                <div class='ui two button attached buttons'>
                    <button class='ui basic blue button' @click="isEditing=false">
                        Close
                    </button>
                </div>
            </div>
        </div>
        <div class='ui bottom attached green basic button' v-show="!isEditing && todo.done" disabled>
            Completed
        </div>
        <div class='ui bottom attached red basic button' v-show="!isEditing && !todo.done" @click="completeTodo(todo)">
            Pending
        </div>
    </div>
</template>
</template>
<script>
export default {
    data() {
        return {
            isEditing: false
        }
    },
    methods:{
        deleteTodo(todo){
            this.$emit('delete-todo', todo)
        },
        completeTodo(todo) {
            this.$emit('complete-todo', todo);
        }
    },
    props: ['todo']

}
</script>
<style>

</style>