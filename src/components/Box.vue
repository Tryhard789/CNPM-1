<template>
	<div @click="$emit('change-filter',type.id)">
		<div>
			{{type.name}}
		</div>
	</div>
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
