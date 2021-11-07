<template>
	<div class="">
		<b-nav class="justify-content-around nav-bar">
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

<style type="text/css" media="screen">
	.nav-bar {
		background-color: white;
		box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
		color: black;
	}
	.container-fluid {
		padding: 0 !important;
		background-color: #DDDDDD;
	}
	.cart {
		background-color: white;
	}
	.menu {
		padding: 0 !important;
	}
</style>
