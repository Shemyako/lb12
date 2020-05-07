<template>
	<div>
		<p>Имя: {{name}}</p>
		<p>Фамилия: {{surname}}</p>
		<p>Должность: {{type}}</p>
	</div>
</template>

<script>
export default{
	data(){
		return{
			name: "Иван",
			surname: "Иванов",
			type: "Уборщик"
		}
	}
}
</script>