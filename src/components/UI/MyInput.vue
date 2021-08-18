<template>
<input class="input" :value="modelValue" @input="updateInput" type="text">
</template>

<script >
export default{
	name:'my-input',
	props:{
		modelValue:[String,Number]
	},
	methods:{
		updateInput(event){
			this.$emit('update:modelValue',event.target.value)
		}
	}
}
</script>

<style  scoped>
.input{
	padding: 10px;
	width: 100%;
	margin-top: 10px;
}
</style>