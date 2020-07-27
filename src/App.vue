<template>
	<div id="app">
		<h1>Tarefas</h1>
		<Progresso v-if="tarefas.length > 0" :progresso="progresso"></Progresso>
		<NovaTarefa @NovaTarefa="adicionarTarefa($event)"></NovaTarefa>
		<ListaTarefas v-if="tarefas.length > 0" :tarefas="tarefas"
			@alterarSituacao="alterarSituacao($event)" 
			@deletarTarefa="deletarTarefa()"></ListaTarefas>
		<h3 v-if="tarefas.length == 0">Sua vida está de boaçaaa ;)</h3>
	</div>
</template>

<script>
import ListaTarefas from './components/ListaTarefas.vue'
import NovaTarefa from './components/NovaTarefa.vue'
import Progresso from './components/Progresso.vue'

export default {
	components: {ListaTarefas, NovaTarefa, Progresso},
	data(){
		return {
			tarefas: []
		}
	},
	computed: {
		progresso(){
			const total = this.tarefas.length
			const pendentes = this.tarefas.filter(t => t.situacao).length
			return Math.round((pendentes/total) * 100) || 0
		}
	},
	watch: {
		tarefas: {
			deep: true,
			handler(){
				localStorage.setItem('tarefas', JSON.stringify(this.tarefas))
			}
		}
	},
	methods: {
		adicionarTarefa(tarefa){
			const verificaIgual = t => t.nome === tarefa.nome
			const novoNome = this.tarefas.filter(verificaIgual).length == 0

			if(novoNome){
				this.tarefas.push({
					nome: tarefa.nome,
					situacao: false
				})
			}else{
				alert("Essa tarefa ja foi adicionada !!")
			}

		},
		deletarTarefa(i){
			this.tarefas.splice(i, 1)
		},
		alterarSituacao(i){
			this.tarefas[i].situacao = !this.tarefas[i].situacao
		}
	},
	created() {
		const json = localStorage.getItem('tarefas')
		const array = JSON.parse(json)
		if(Array.isArray(array)){
			this.tarefas = JSON.parse(json) || []
		}
	}
}
</script>

<style>
	body {
		font-family: 'Lato', sans-serif;
		background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
		color: #FFF;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 300;
		font-size: 3rem;
	}
</style>
