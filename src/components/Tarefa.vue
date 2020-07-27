<template>
    <div @click="$emit('alterarSituacao', tarefa)" class="tarefa" :class="estadoClasse">
        <span @click.stop="$emit('deletarTarefa', tarefa)" class="fechar">X</span>
        <p>{{tarefa.nome}}</p>
    </div>
</template>

<script>
export default {
    props: {
        tarefa: {
            type: Object,
            required: true
        }
    },
    computed: {
        estadoClasse(){
            return {
                pendente: !this.tarefa.situacao,
                concluida: this.tarefa.situacao
            }
        }
    }
}
</script>

<style>
    .tarefa{
        position: relative;
        box-sizing: border-box;
        width: 350px;
        height: 150px;
        padding: 10px;
        border-radius: 10px;
        font-size: 2rem;
        font-weight: 300;
        cursor: pointer;
        user-select: none;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .pendente{
        background-color: red;
        border-left: 12px solid #4e0404;
        color: white;
    }
    .concluida{
        background-color: green;
        border-left: 12px solid #0733078e;
        color: white;   
        text-decoration: line-through;
    }
    .pendente .fechar{
        background-color: rgb(133, 11, 11);
    }
    .concluida .fechar{
        background-color: rgb(19, 88, 19);
    }
    .fechar{
        position:absolute;
        right: 10px;
        top: 10px;
        font-size: 0.9rem;
        font-weight: 600;
        height: 20px;
        width: 20px;
        border-radius: 10px;
        display: flex;
        justify-content: center;
    }
</style>
