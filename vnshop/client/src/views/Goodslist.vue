<template>
	<div>
		<NavHeader></NavHeader>
		<NavBread>商品列表</NavBread>
		
			<!--<div class="site-header" style="clear:both;">
		        <div class="container">
		            <div class="header-logo">
		                <a href="index.php" title="小米官网"><img src="/static/img/logo.png" /></a>
		            </div>
		            <div class="header-nav">
		                <ul class="nav-list">
		                    <li class="nav-category">
		                        <a class="btn-category-list" href="catalog.php" style="display:none;">全部商品分类</a>
		                    </li>
		                    <li class="nav-item">
		                        <a class="link" href="category.php?id=76"><span>电子产品</span></a>
		                        <div class='item-children'>
		                            <div class="container">
		                                <ul class="children-list clearfix">
		                                    <li class="first">
		                                        <div class="figure figure-thumb">
		                                            <a href="goods.php?id=27"><img src="" alt="小米电视2 40英寸"></a>
		                                        </div>
		                                        <div class="title"><a href="goods.php?id=27">小米电视2 40英寸</a></div>
		                                        <p class="price">2200<em>元</em>元</p>
		                                    </li>
		                                </ul>
		                            </div>
		                        </div>
		                    </li>
		                </ul>
		            </div>
		            <div class="topbar-cart" id="ECS_CARTINFO">
		                <a class="cart-mini " href="flow.php">
		                    <i class="iconfont">&#xe60c;</i> 购物车
		                    <span class="mini-cart-num J_cartNum" id="hd_cartnum">(0)</span>
		                </a>
		            </div>
		            <div class="topbar-info J_userInfo" id="ECS_MEMBERZONE">
		                <a class="link" href="user.php" rel="nofollow">登录</a>
		                <span class="sep">|</span>
		                <a class="link" href="user.php?act=register" rel="nofollow">注册</a>
		            </div>
		        </div>
		        <div id="J_navMenu" class="header-nav-menu" style="display: none;">
		            <div class="container"></div>
		        </div>
		    </div>-->
		    
		    <!--<div class="nav-breadcrumb-wrap">
		        <div class="container">
		            <nav class="nav-breadcrumb">
		                <a href="/">Home</a>
		                <span>Goods</span>
		            </nav>
		        </div>
		    </div>-->
		    <div class="accessory-result-page accessory-page">
		        <div class="container">
		            <div class="filter-nav">
		                <span class="sortby">Sort by:</span>
		                <a href="javascript:void(0)" class="default cur">Default</a>
		                <a href="javascript:void(0)" class="price" @click="sort">Price <svg class="icon icon-arrow-short"><use xlink:href="#icon-arrow-short"></use></svg></a>
		                <a href="javascript:void(0)" class="filterby stopPop">Filter by</a>
		            </div>
		            <div class="accessory-result">
		                <!-- filter -->
		                <div class="filter stopPop" id="filter">
		                    <dl class="filter-price">
		                        <dt>Price:</dt>
		                        <dd><a href="javascript:void(0)">All</a></dd>
		                        <dd>
		                            <a href="javascript:void(0)">0 - 100</a>
		                        </dd>
		                        <dd>
		                            <a href="javascript:void(0)">100 - 500</a>
		                        </dd>
		                        <dd>
		                            <a href="javascript:void(0)">500 - 1000</a>
		                        </dd>
		                        <dd>
		                            <a href="javascript:void(0)">1000 - 2000</a>
		                        </dd>
		                    </dl>
		                </div>
		
		                <!-- search result accessories list -->
		                <div class="accessory-list-wrap">
		                    <div class="accessory-list col-4">
		                        <ul>
		                            <li v-for="(item,index) in goods" :key="index">
                                <div class="pic">
                                    <a href="#"><img :src="'/static/img/' + item.productImage" alt=""></a>
                                </div>
                                <div class="main">
                                    <div class="name">{{item.productName}}</div>
                                    <div class="price">{{item.salePrice}}</div>
                                    <div class="btn-area">
                                        <a href="javascript:;" class="btn btn--m">加入购物车</a>
                                    </div>
                                </div>
                            </li>
		                        </ul>
		                    </div>
		                </div>
		            </div>
		        </div>
		    </div>
		    
		<NavFooter/>
		    
		
	</div>
</template>

<script>
	//import '../../static/css/base.css'
	//import '../../static/css/product.css'
	import NavHeader from '@/components/Header'
	import NavFooter from '@/components/Footer'
	import NavBread from '@/components/NavBread'
	import axios from 'axios'
	export default{
		components:{
			NavHeader:NavHeader,
			NavFooter:NavFooter,
			NavBread:NavBread
		},
		data(){
			return {
				goods:{},
				sortFlag:true
			}
		},
		created(){
			this.getGoodsList();
		},
		methods:{
			getGoodsList(){
				/*axios.get('goods').then(res=>{
                     this.goods = res.data.data;
                 })*/
                let sort = this.sortFlag ? 1: -1;
                axios.get('/goods/list',{params:{sort:sort}}).then( res=> {
                     this.goods = res.data.result;
                })
			},
			sort(){
				this.sortFlag = !this.sortFlag;
				this.getGoodsList();
			}
			
		}
		
	}
</script>
	
	
<style>
</style>