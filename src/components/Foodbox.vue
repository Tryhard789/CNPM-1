<template>
	<div class="container my-5">
		<b-card :img-src="food.img" :img-alt="food.name" img-top>
			<b-card-text>
				Price: ${{food.price}}
				<button class="float-right btn btn-danger" 
						@click="OpenModal"
					> 
					<span >
						<b-icon icon="cart"></b-icon>
				</span>
					Buy
				</button>
			</b-card-text>
		</b-card>
		
	</div>
</template>
<script>


export default {
	name:'FoodBox',
	props:{
		food:Object,
	},
	
	methods:{
		OpenModal(){
			this.$emit('openmodal',this.food.id)
		},

	},
	emits:['openmodal'],
}
</script>