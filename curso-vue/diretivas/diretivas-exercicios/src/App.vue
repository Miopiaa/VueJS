<template>
	<div id="app">
		<h1>Diretivas</h1>
		<hr>
		<p v-text="'Usando diretiva v-text'"></p>
		<p v-html="'Usando diretiva <strong>v-html</strong>'"></p>
		<hr>
		<p v-destaque:fundo="'blue'">Usando diretiva personalizada</p>
		<p v-destaque="cor">Usando diretiva personalizada</p>
		<p v-destaque.atrasar="cor">Usando diretivas personalizada</p>
		<hr>
		<p v-destaque-local:fundo.atrasar="'blue'">Usando diretiva personalizada</p>
		<p v-destaque-local.atrasar.alternar="cor">Usando diretiva personalizada</p>
	</div>
</template>

<script>
export default {
	components: { },
	directives: {
		'destaque-local': {
				bind(el, binding, vnode) {
				const aplicarCor = cor => {
					if(binding.arg === 'fundo') {
						el.style.backgroundColor = cor
					} else {
						el.style.color = cor
					}
				}
				//el.style.backgroundColor = 'lightgreen'

				let atraso = 0
				if(binding.modifiers['atrasar']) atraso = 300
 
				const cor1 = binding.value
				const cor2 = 'purple'
				let corAtual = cor1
 
 				setTimeout(() => {
					if(binding.modifiers['alternar']) {
						setInterval(() => {
				  		}, 1000)
					} 
					aplicarCor(binding.value)  
				}, atraso)
			}
		}
	},
	data() {
		return {
			cor: 'red'
		}
	}
}
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
	font-size: 2.5rem;
}
</style>
