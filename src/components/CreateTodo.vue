<template>
    <div class='ui basic content center aligned segment'>
        <button class='ui basic button icon' @click="isCreating=true" v-show="!isCreating">
            <i class='plus icon'></i>
        </button>
        <div class='ui centered card' v-show="isCreating">
            <div class='content'>
                <div class='ui form'>
                    <div class='field'>
                        <label>Title</label>
                        <input type='text' v-model="titleText">
                    </div>
                    <div class='field'>
                        <label>Project</label>
                        <input type='text' v-model="projectText">
                    </div>
                    <div class="ui buttons">
                        <button class="ui positive button" @click="sendForm">Create</button>
                        <div class="or"></div>
                        <button class="ui button" @click="isCreating=false">Cancel</button>   
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            titleText: '',
            projectText: '',
            isCreating: false,
        }
    },
    methods: {
        sendForm() {
            const title = this.titleText;
            const project = this.projectText;
            if (title.length > 0 && project.length > 0) {
                this.$emit('add-todo', {title, project, done: false})
                this.titleText = ''
                this.projectText = ''
            }
            this.isCreating = false
        }
    }
};
</script>
<style>

</style>