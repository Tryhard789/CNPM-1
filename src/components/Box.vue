<template>

	<b-card @click="$emit('change-filter',type.id)" :img-src="type.src" :img-alt="type.name" img-top 
		class=" center border-2" >
		<b-card-text class="text-align-center">

	<div @click="$emit('change-filter',type.id)">
		<div>

			{{type.name}}
		</div>
	</div>
	</b-card-text>
	</b-card>
</template>
<script>
export default {
	name:'Box',
	props:{
		type:Object,
	},
	emits:['change-filter'],
}
</script>
<style  scoped>
	b-card{
		max-width: 5rem !important;
		overflow: hidden !important;
	}

</style>


