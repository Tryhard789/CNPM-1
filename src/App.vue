<template>
<div>
  <b-container fluid>
  <b-row>
  <b-col sm="8" cols="12">
  <Menu :Filt="filter" :FoodList="List" :Types="Types" 
    @change-filter="changeFilter"
    @openmodal="getModal"
  />
  </b-col>
  <b-col sm="4" cols="12">  
    <div v-for="food in Cart" :key="food.id"><h1 v-if="food.qtity>0">{{food.name}} {{food.price}}</h1></div>
    <div>total: {{total}}</div>
  </b-col>
  </b-row>
  </b-container>
  <ModalFood :food="food" @close="closeModal" v-show="this.openModal" @order-up="addFood" />
</div>
</template>

<script>
import Menu  from './components/menu.vue'
import ModalFood from './components/Modal.vue'

export default {
  name: 'App',
  components: {
    Menu,ModalFood
  },
  data(){
    return{
      Types:[],
      List:[],
      filter:Number,
      Cart:[],
      food:Object,
      openModal:Boolean,
      total:Number
    }
  },
  created(){
    this.Types=[
      {id:1,name:'all',src:'sdfs'},
      {id:2,name:'Sea food',src:'sdfsf'},
      {id:3,name:'Desert',src:'sdfs'},
      {id:4,name:'Juice',src:'sdfs'},
      {id:5,name:'Soft drink',src:'sdf'},
    ]
    this.List=[
      {id:1,name:'coca',type:5,price:50, qtity:0,img:'https://picsum.photos/600/300/?image=25',
        side:{'fried':false,'salad':false,'pop':false}},
      {id:2,name:'Apple juic',type:4,price:80, qtity:0,img:'asdfa',
        side:{'fried':false,'salad':false,'pop':false}},
      {id:3,name:'Cup cake',type:3,price:60, qtity:0,img:'asdfa',
        side:{'fried':false,'salad':false,'pop':false}},
      {id:4,name:'Fish',type:2,price:100, qtity:0,img:'asdfa',
        side:{'fried':false,'salad':false,'pop':false}},
      {id:5,name:'Steake',type:6,price:90, qtity:0,img:'asdfa',
        side:{'fried':false,'salad':false,'pop':false}},
    ]
    this.Cart=[]
    this.filter=this.Types[0].id
    this.food=this.List[0]
    this.openModal=false;
    this.total=0
  },
  methods:{
    changeFilter(id){
      this.filter=id
      console.log(this.filter)
    },
    addFood(food){
      const index = this.List.findIndex((x)=>{return x.id===food.id })
      let newList=[...this.List]
      
      newList[index]=food
      this.List=[...newList]
      const index_nd=this.Cart.findIndex((type)=>type.id===food.id)
      console.log (index_nd)
      if( index_nd<0){
        this.Cart=[...this.Cart,food]
      }else {
        this.Cart[index_nd]=food
        
      }
      console.log(this.Cart)
      this.total=0
      this.Cart.forEach(element => {
        this.total+=element.price*element.qtity
      });
      let temp=this.Cart.filter((item)=>item.qtity>0)
      this.Cart=temp
      console.log(this.Cart)
    },
    closeModal(){
      this.openModal=false;
    },
    getModal(id){
      const index=this.List.findIndex((food)=>food.id===id)
      this.food=this.List[index]
      this.openModal=true
    }

  }
}
</script>

<style>

</style>
