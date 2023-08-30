<script setup>
import { ref } from 'vue'

const current = ref('')

function clear() {
	current = ''
}
</script>

<template>
	<div class="calculator">
		<div class="display">
			{{ current || 0 }}
		</div>
		<div @click="clear" class="btn">C</div>
		<div @click="sign" class="btn operator">+/-</div>
		<div class="btn operator">%</div>
		<div class="btn operator">/</div>
		<div class="btn">7</div>
		<div class="btn">8</div>
		<div class="btn">9</div>
		<div class="btn operator">*</div>
		<div class="btn">4</div>
		<div class="btn">5</div>
		<div class="btn">6</div>
		<div class="btn operator">-</div>
		<div class="btn">1</div>
		<div class="btn">2</div>
		<div class="btn">3</div>
		<div class="btn operator">+</div>
		<div class="btn zero">0</div>
		<div class="btn">.</div>
		<div class="btn operator">=</div>
		<div class="btn"></div>
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
