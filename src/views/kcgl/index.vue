<template>
    <div class="app">
			<h1>产品列表</h1>
			<ul>
				<!--插值表达式-->
				<li v-for="item in product" :key='item.id'>{{item.name}}-{{item.price}}<button :disabled="item.amount==0" @click="add(item)">加入购物车</button></li>
			</ul>
			<h1>购物车</h1>
			<ul>
				<li v-for="item in shopping"  :key='item.id'>{{item.name}}:{{item.quantity}}x{{item.price}}={{item.quantity*item.price}}</li>
			</ul>
			<p>总和：{{totalprice}}</p>
		</div>
</template>
<script>

export default({
    data(){
        return {
            product: [{
                "id":"001",
                "name":"iPhone12",
                "price":8900,
                "amount":5,
                "quantity":1,
                "total":8900,
                "check":false
            },{
                "id":"002",
                "name":"iPhone11",
                "price":6000,
                "amount":8,
                "quantity":1,
                "total":6000,
                "check":false
            },{
                "id":"003",
                "name":"iPhoneMax10",
                "price":3000,
                "amount":10,
                "quantity":1,
                "total":3000,
                "check":false
            },{
                "id":"004",
                "name":"iPhoneMin9",
                "price":2000,
                "amount":12,
                "quantity":1,
                "total":2000,
                "check":false
            }],//存放json
			shopping: []//存放加入购物车
        }
		},
        methods: {
				add(product) {
					//判断当前值的id是否和点击产品id相等
					let p = this.shopping.find(value => value.id == product.id)
					console.log(p)
					product.amount--//点击的时候总数量-1
					if(p) {
						p.quantity++
					} else {
						let {name,id,price} = product
						this.shopping.push({
							name,
							id,
							price,
							quantity: 1
						})
					}
				}
				
			},
			computed:{
				totalprice(){
					//reduce计算数组元素相加后的总会
					return this.shopping.reduce((sum,value)=>{
						sum+=value.quantity*value.price
						return sum
					},0)
				}
			}
})
</script>
<style scoped>
.app{
    width: 60%;
    height: 400px;
    margin: 0 auto;
    background: #fff;
}
</style>
