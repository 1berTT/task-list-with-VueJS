<template>
    <div class="nova-tarefa">
        <input v-model="nome" @keydown.enter="adicionar()" 
            class="form-element" placeholder="Nova tarefa?" type="text">
        <button class="form-element" @click="adicionar()">+</button>
    </div>
</template>

<script>
export default {
    data(){
        return {
            nome: ''
        }
    },
    methods: {
        adicionar(){
            this.$emit('NovaTarefa', {nome: this.nome})
            this.nome = ''
        }
    }
}
</script>

<style>
    .nova-tarefa{
        margin: 35px;
    }
    .form-element{
        outline: none;
        font-size: 2rem;
        border: 1px solid rgba(255, 255, 255, 0.377);
        padding: 5px 10px 8px;
        color: white;
    }
    input.form-element{
        width: 500px;
        background: #FFF2;
        border-top-left-radius: 8px;
        border-bottom-left-radius: 8px; 
    }
    button.form-element{
        background-color: blue;
        border-top-right-radius: 8px;
        border-bottom-right-radius: 8px; 
        cursor: pointer;
    }
</style>
