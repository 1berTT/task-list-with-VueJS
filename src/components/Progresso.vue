<template>
    <div class="progresso">
        <span class="porcentagem">{{progresso}}%</span>
        <div class="qtd" :style="{width: progresso + '%'}"></div>
    </div>
</template>

<script>
export default {
    props: {
        progresso: {
            type: Number,
            default: 0
        }
    }
}
</script>

<style>
    .progresso{
        position: relative;
        width: 80%;
        border: 1px solid white;
        color: white;
        border-radius: 8px;
        margin-bottom: 15px;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .porcentagem{
       z-index: 1;
       font-size: 1.5rem;
    }
    .qtd{
        position: absolute;
        border-radius: 8px;
        height: 100%;
        background-color: green;
        align-self: flex-start;
    }
</style>
