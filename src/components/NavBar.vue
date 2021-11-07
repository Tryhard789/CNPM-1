<template>
	<div>
		<b-nav class="border justify-content-center">
			<b-nav-item :key="type.id" v-for="type in Types">
				<Box :type="type" @change-filter="$emit('change-filter',type.id)"/>
			</b-nav-item>
		</b-nav>
	</div>
</template>
<script>
import Box from './Box.vue'
export default {
	name:'NavBar',
	components:{
		Box,
	},
	props:{
		Types:Array
	},
	emits:['change-filter'],
}
</script>