<script setup>
import { ref } from 'vue'

const current = ref('')
const history = []
const solve   = ref('')
const state   = ref(true)

function clear() {
	state.value   = true
	current.value = ''
}

function sign() {
	current.value = current.value.charAt(0) === '-'  ? 
		current.value.slice(1) : `-${current.value}`
}

function percent() {
	current.value = `${parseFloat(current.value)/100}`
}

function append(number) {
	current.value = `${current.value}${number}`
}

function dot() {
	if(current.value.indexOf('.') === -1){
		append('.')
	}
}

function equal() {
	solve.value   = current.value + '=' 
	current.value = eval(current.value)
	solve.value   = solve.value + `${current.value}`
	history.push(solve.value)
}

function histories() {
	state.value   = false
	current.value = history.value 
}
</script>

<template>
	<div class="calculator">
		<div class="display">
			<div v-if="state">
				{{ current || 0 }}
			</div>
			<div v-else>
				<ul>
					<li v-for="(hist, index) in history" :key="index">
						{{ hist }}
					</li>
				</ul>
			</div>
		</div>
		<div @click="clear" class="btn">C</div>
		<div @click="sign" class="btn operator">+/-</div>
		<div @click="percent" class="btn operator">%</div>
		<div @click="append('/')" class="btn operator">/</div>
		<div @click="append('7')" class="btn">7</div>
		<div @click="append('8')" class="btn">8</div>
		<div @click="append('9')" class="btn">9</div>
		<div @click="append('*')" class="btn operator">*</div>
		<div @click="append('4')" class="btn">4</div>
		<div @click="append('5')" class="btn">5</div>
		<div @click="append('6')" class="btn">6</div>
		<div @click="append('-')" class="btn operator">-</div>
		<div @click="append('1')" class="btn">1</div>
		<div @click="append('2')" class="btn">2</div>
		<div @click="append('3')" class="btn">3</div>
		<div @click="append('+')" class="btn operator">+</div>
		<div @click="append('0')" class="btn zero">0</div>
		<div @click="dot" class="btn">.</div>
		<div @click="equal" class="btn operator">=</div>
		<div @click="histories" class="btn">history</div>
	</div> 	
</template>

<style scoped>
.calculator {
	grid-template-columns: repeat(4, 1fr);
	cursor: pointer;
	margin: 0 auto;
	width: 480px;
	font-size: 40px;
	display: grid;
	grid-template-rows: minmax(50px, auto);
}
.display {
	grid-column: 1 / 5;
	background-color: #333;
	color: white;
}
.btn {
	background-color: #f2f2f2;
	border: 1px solid #999;
}

.zero {
	grid-column: 1 / 3;
}

.operator {
	background-color: orange;
	color: white;

}
</style>
