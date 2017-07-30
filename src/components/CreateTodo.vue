<template>
    <div class='ui basic content center aligned segment'>
        <button class='ui basic button icon' v-on:click="openForm" v-show="!isCreating">
            <i class='plus icon'></i>
        </button>
        <div class='ui centered card' v-show="isCreating">
            <div class='content'>
                <div class='ui form'>
                    <div class='field'>
                        <label>Titulo</label>
                        <input v-model="titleText" type='text'>
                    </div>
                    <div class='field'>
                        <label>Proyecto</label>
                        <input v-model="projectText" type='text'>
                    </div>
                    <div class='ui two button attached buttons'>
                        <button class='ui basic blue button' @click="sendForm">
                        Create
                        </button>
                        <button class='ui basic red button' @click="closeForm">
                        Cance
                        </button>
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
                isCreating: false,
                titleText: '',
                projectText: '',
            };
        },
        methods: {
            openForm(){
                this.isCreating = true;
            },
            sendForm(){
                if(this.titleText.length > 0 && this.projectText.length > 0){
                    const title = this.titleText;
                    const project = this.projectText;
                    this.$emit('create', {
                        title,
                        project,
                        done: false,
                    });
                    this.titleText = '';
                    this.projectText = '';
                    this.isCreating = false;
                }
            },
            closeForm(){
                this.isCreating = false;
            }
        }
    }
</script>