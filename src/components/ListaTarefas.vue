<template>
    <div class="tarefas">
        <template>
            <Tarefa v-for="(tarefa, i) in tarefas" :key="tarefa.nome" 
                @deletarTarefa="$emit('deletarTarefa', i)" 
                @alterarSituacao="$emit('alterarSituacao', i)" :tarefa="tarefa"></Tarefa>
        </template>
    </div>
</template>

<script>
import Tarefa from './Tarefa.vue'

export default {
    components: {Tarefa},
    props: {
        tarefas: {
            type: Array,
            required: true
        }
    }
}
</script>

<style>
    .tarefas{
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }
    .tarefas .tarefa{
        margin: 10px;
    }
</style>
