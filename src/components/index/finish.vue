<template>
	<main class="finish">
		<!--头部-->
		<header class="user-header" id="header">
			<div class="head-left">
				<i class="iconfont" @click="$router.back(-1)" id="backicon">&#xe631;</i>
				<h1 id="headword">完本</h1>
			</div>
			<div class="head-right">
				<i class="iconfont" id="searchicon" @click="yes()">&#xe62f;</i>
				<i class="iconfont" @click="show()" id="menuicon">&#xe62c;</i>
			</div>
		</header>
		<!--搜索页-->
		<div class="search-popup" id="searchPopup">
			<div class="search-header">
				<form class="search-form">
					<div class="search-area">
						<i class="iconfont">&#xe62f;</i>
						<input type="search" class="search-input" placeholder="" v-model="inPut" id="searchInput"/>
					</div>
					<span class="search-cancel" @click="no()">取消</span>
				</form>
			</div>
			<div class="search-history">
				<div class="search-title-bar">
					<h5 class="search-title">大家都在搜</h5>
				</div>
				<div class="search-tags">
					<router-link to="/details" class="btn-line">试婚老公，要给力</router-link>
					<router-link to="/details" class="btn-line">腹黑狂妃太凶猛</router-link>
					<router-link to="/details" class="btn-line">凤帝九倾</router-link>
					<router-link to="/details" class="btn-line">你好，痞子老公！</router-link>
					<router-link to="/details" class="btn-line">公子有疾我有药</router-link>
				</div>
			</div>
		</div>
		<!--导航-->
		<div class="guide" id="guide">
			<transition enter-active-class="animated fadeIn" leave-active-class="animated fadeOut">
				<span class="guide-overlay" v-show="isTrue" @click="show()"></span>
			</transition>
			<transition enter-active-class="animated slideInDown" leave-active-class="animated slideOutUp">
				<div class="guide-content" v-show="isTrue">
					<ul class="guide-nav">
						<li class="guide-nav-li">
							<router-link to="/index" class="guide-nav-a">
								<i class="icon icon-home"></i>
								<h4 class="guide-nav-h">首页</h4>
							</router-link>
						</li>
						<li class="guide-nav-li">
							<router-link to="/category" class="guide-nav-a">
								<i class="icon icon-sort"></i>
								<h4 class="guide-nav-h">分类</h4>
							</router-link>
						</li>
						<li class="guide-nav-li">
							<router-link to="/rank" class="guide-nav-a">
								<i class="icon icon-rank"></i>
								<h4 class="guide-nav-h">排行榜</h4>
							</router-link>
						</li>
						<li class="guide-nav-li">
							<router-link to="/welfare" class="guide-nav-a">
								<i class="icon icon-fuli"></i>
								<h4 class="guide-nav-h">福利</h4>
							</router-link>
						</li>
						<li class="guide-nav-li">
							<router-link to="/finish" class="guide-nav-a">
								<i class="icon icon-end"></i>
								<h4 class="guide-nav-h">完本</h4>
							</router-link>
						</li>
						<li class="guide-nav-li">
							<router-link to="/user" class="guide-nav-a">
								<i class="icon icon-account"></i>
								<h4 class="guide-nav-h">账户</h4>
							</router-link>
						</li>
					</ul>
					<div class="guide-footer">
						<router-link to="/bookshelf" class="btn-primary">我的书架</router-link>
					</div>
				</div>
			</transition>
		</div>
		<!--最新完结-->
		<div class="module">
			<div class="module-header">
				<div class="module-header-l">
					<h3 class="module-title">最新完结</h3>
				</div>
				<div class="module-header-r">
					<router-link to="/more" class="module-header-btn">
						更多<i class="iconfont">&#xe627;</i>
					</router-link>
				</div>
			</div>
			<ol class="book-ol book-ol-normal">
				<li class="book-li" v-for="(item,index) in data.newend">
					<router-link to="/details" class="book-layout">
						<img :src="item.src" alt="" class="book-cover"/>
						<div class="book-cell">
							<h4 class="book-title">{{item.title}}</h4>
							<p class="book-desc">{{item.desc}}</p>
							<div class="book-meta">
								<div class="book-meta-l">
									<i class="iconfont">&#xe608;</i>
									<span class="book-author">{{item.author}}</span>
								</div>
								<div class="book-meta-r">
									<span class="tag-small-group origin-right">
										<span class="tag-small yellow">{{item.yellow}}</span>
										<span class="tag-small red">{{item.red}}</span>
										<span class="tag-small blue">{{item.blue}}</span>
									</span>
								</div>
							</div>
						</div>
					</router-link>
				</li>
			</ol>
		</div>
		<!--经典必读-->
		<div class="module">
			<div class="module-header">
				<div class="module-header-l">
					<h3 class="module-title">经典必读</h3>
				</div>
				<div class="module-header-r">
					<router-link to="/more" class="module-header-btn">
						更多<i class="iconfont">&#xe627;</i>
					</router-link>
				</div>
			</div>
			<ol class="book-ol book-ol-normal">
				<li class="book-li" v-for="(item,index) in data.classic">
					<router-link to="/details" class="book-layout">
						<img :src="item.src" alt="" class="book-cover"/>
						<div class="book-cell">
							<h4 class="book-title">{{item.title}}</h4>
							<p class="book-desc">{{item.desc}}</p>
							<div class="book-meta">
								<div class="book-meta-l">
									<i class="iconfont">&#xe608;</i>
									<span class="book-author">{{item.author}}</span>
								</div>
								<div class="book-meta-r">
									<span class="tag-small-group origin-right">
										<span class="tag-small yellow">{{item.yellow}}</span>
										<span class="tag-small red">{{item.red}}</span>
										<span class="tag-small blue">{{item.blue}}</span>
									</span>
								</div>
							</div>
						</div>
					</router-link>
				</li>
			</ol>
		</div>
		<!--畅销完本-->
		<div class="module">
			<div class="module-header">
				<div class="module-header-l">
					<h3 class="module-title">畅销完本</h3>
					<span class="module-title-desc">一周热销完本书</span>
				</div>
				<div class="module-header-r">
					<router-link to="/more" class="module-header-btn">
						更多<i class="iconfont">&#xe627;</i>
					</router-link>
				</div>
			</div>
			<ol class="book-ol book-ol-normal">
				<li class="book-li" v-for="(item,index) in data.bestend">
					<router-link to="/details" class="book-layout">
						<img :src="item.src" alt="" class="book-cover"/>
						<div class="book-cell">
							<h4 class="book-title">{{item.title}}</h4>
							<p class="book-desc">{{item.desc}}</p>
							<div class="book-meta">
								<div class="book-meta-l">
									<i class="iconfont">&#xe608;</i>
									<span class="book-author">{{item.author}}</span>
								</div>
								<div class="book-meta-r">
									<span class="tag-small-group origin-right">
										<span class="tag-small yellow">{{item.yellow}}</span>
										<span class="tag-small red">{{item.red}}</span>
										<span class="tag-small blue">{{item.blue}}</span>
									</span>
								</div>
							</div>
						</div>
					</router-link>
				</li>
			</ol>
		</div>
		<!--尾部-->
		<footer>
			<div class="footer-link">
				<router-link to="/index" class="footer-link-a">书架</router-link>
				<router-link to="/index" class="footer-link-a">充值</router-link>
				<router-link to="/index" class="footer-link-a">帮助</router-link>
				<router-link to="/index" class="footer-link-a">客户端</router-link>
			</div>
			<div class="footer-copy">Copyright © 2002-2019 m.readnovel.com</div>
		</footer>
		<!--返回顶部-->
		<div class="footer-backtop-circle" @click="backTop()" v-show="hide">
			<i class="iconfont">&#xeb8e;</i>
		</div>
	</main>
</template>

<script>
	export default{
		data(){
			return{
				isTrue:false,
				inPut:"",
				data:[],
				hide:false
			}
		},
		methods:{
			show(){
				this.isTrue=!this.isTrue;
				console.log(this.isTrue)
				if(this.isTrue==true){
					menuicon.innerHTML="&#xe630;"
					guide.style.visibility="visible"
				}else if(this.isTrue==false){
					menuicon.innerHTML="&#xe62c;"
					guide.style.visibility="hidden"
				}
			},
			handleScroll(){
				let that = this
			    let scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop
			    that.scrollTop = scrollTop
		    	if(that.scrollTop>=500){
		    		that.hide=true
		    	}else{
		    		that.hide=false
		    	}
			},
			backTop() {
				let that = this
			    let timer = setInterval(() => {
			        let ispeed = Math.floor(-that.scrollTop / 5)
			        window.pageYOffset = document.documentElement.scrollTop = document.body.scrollTop = that.scrollTop + ispeed
			        if (that.scrollTop === 0) {
			          clearInterval(timer)
			        }
			    }, 16)
	       	},
	        yes(){
		    	searchPopup.style.visibility="visible";
		       	searchInput.focus();
		    },
		    no(){
		       	searchPopup.style.visibility="hidden";
		    }
		},
		mounted(){
		  	this.$http.get('./data/finish-data.json')
		  	.then((res)=>{
		  		this.data=res.data;
		  	})
		  	.catch(()=>{
		  		console.log('请求失败了！')
		  	})
		  	.finally(()=>{
		  		console.log('请求结束啦！')
		  	})
		  	window.addEventListener('scroll', this.handleScroll,true);
		},
		destroyed(){
			window.removeEventListener('scroll', this.handleScroll);
		}
	}
</script>

<style scoped="scoped">
	.user-header{
		color: #FF3955;
		background: white;
	}
	.user-header .head-left h1{
		color: #000000;
	}
</style>

<style>
	main.finish{
		background: #F6F7F9;
	}
	/*头部*/
	.user-header{
		width: 100%;
		position: relative;
		box-sizing: border-box;
		overflow: hidden;
		padding-top: 0.7rem;
	}
	.user-header .head-left{
		width: 50%;
		float: left;
		line-height: 1.5rem;
	}
	.user-header .head-left>i{
		margin: 0 0.6rem;
		font-size: 1.5rem;
		opacity: 0.6;
		text-align: center;
		display: inline-block;
		vertical-align: 0.2ex;
	}
	.user-header .head-left h1{
		font-size: 1rem;
		overflow: hidden;
		white-space: nowrap;
		text-overflow: ellipsis;
		font-weight: 400;
		display: inline-block;
	}
	.user-header .head-right{
		float: right;
		padding: 0 0.375rem;
		line-height: 1.5rem;
	}
	.user-header .head-right i{
		font-size: 1.25rem;
		padding: 0 0.375rem;
		opacity: 0.9;
	}
	/*导航*/
	.guide{
		position: fixed;
		left: 0;
		top: 2.5rem;
		right: 0;
		bottom: 0;
		z-index: 3;
		overflow: hidden;
		visibility: hidden;
		transition: visibility 0.25s;
	}
	.guide-overlay{
		position: absolute;
		left: 0;
		right: 0;
		top: 2.75rem;
		bottom: 0;
		background-color: #000000;
		opacity: 0.6!important;
		animation-duration: 0.25s;
	}
	.guide-content{
		position: relative;
		background-color: #FFFFFF;
		overflow: hidden;
		animation-duration: 0.25s;
	}
	.guide-nav{
		text-align: justify;
		font-size: 0;
		overflow: hidden;
	}
	.guide-nav-li{
		width: calc(100%/3);
		margin: 0;
		display: inline-block;
	}
	.guide-nav .guide-nav-a{
		margin: 0.75rem 0;
	}
	.guide-nav-a{
		display: inline-block;
		width: 100%;
		text-align: center;
		font-size: 0.75rem;
		position: relative;
		padding: 1.9rem 0;
	}
	.guide-nav-a>.icon{
		position: absolute;
		left: 0;
		right: 0;
		bottom: 1.625rem;
		margin: auto;
	}
	.icon-home{
		display: block;
		background-image: url(../../assets/img/home-nav.png);
		background-size: 188px 176px;
		background-position: 0px -80px;
		width: 36px;
		height: 36px;
	}
	.icon-sort{
		display: block;
		background-image: url(../../assets/img/home-nav.png);
		background-size: 188px 176px;
		background-position: -120px -40px;
		width: 36px;
		height: 36px;
	}
	.icon-rank{
		display: block;
		background-image: url(../../assets/img/home-nav.png);
		background-size: 188px 176px;
		background-position: 0px -40px;
		width: 36px;
		height: 36px;
	}
	.icon-fuli{
		display: block;
		background-image: url(../../assets/img/home-nav.png);
		background-size: 188px 176px;
		background-position: -80px -80px;
		width: 36px;
		height: 36px;
	}
	.icon-end{
		display: block;
		background-image: url(../../assets/img/home-nav.png);
		background-size: 188px 176px;
		background-position: -120px 0px;
		width: 36px;
		height: 36px;
	}
	.icon-account{
		display: block;
		background-image: url(../../assets/img/home-nav.png);
		background-size: 188px 176px;
		background-position: -40px 0px;
		width: 36px;
		height: 36px;
	}
	.guide-nav-h{
		position: absolute;
		left: 0;
		right: 0;
		bottom: 0.1875rem;
		color: #1A1A1A;
		font-weight: normal;
	}
	.guide-footer{
		text-align: center;
		margin-top: 1rem;
		margin-bottom: 1.5rem;
	}
	.btn-primary{
		width: 75%;
		display: inline-block;
		padding-left: 2ch;
		padding-right: 2ch;
		background-color: #FF3955;
		color: #FFFFFF;
		font-size: 0.875rem;
		border-radius: 99px;
		line-height: 2.25rem;
		text-align: center;
	}
	/*最新完结*/
	.module{
		margin: 0.75rem 0;
		background-color: #FFFFFF;
	}
	.module-header{
		border-top: 1rem solid transparent;
		padding: 0 1rem;
		overflow: hidden;
	}
	.module-header-l{
		float: left;
	}
	.module-header-r{
		float: right;
	}
	.module-title{
		display: inline;
		color: #1a1a1a;
		font-size: 1rem;
	}
	.module-title::before{
		content: "";
		width: 0.625rem;
		height: 1em;
		display: inline-block;
		box-sizing: border-box;
		border-left: 2px solid #FF3955;
		vertical-align: -.22ex;
	}
	.module-title-desc{
		margin-left: 0.5rem;
		color: #808080;
		font-size: 0.8125rem;
	}
	.module-header-btn{
		line-height: 1.5rem;
		padding: 0.5rem 0.5rem 0.5rem 0.75rem;
		color: #808080;
		font-size: 0.8125rem;
	}
	.module-header-btn>i{
		display: inline-block;
		text-align: center;
		vertical-align: -0.2ex;
	}
	.book-layout{
		display: block;
		padding: 1rem;
		position: relative;
		overflow: hidden;
		transition: padding-left 0.15s;
	}
	.book-li::after{
		content: "";
		display: block;
		border-bottom: 1px solid #f0f1f2;
		margin-left: 1rem;
		margin-top: -1px;
	}
	.book-li:last-child::after{
		display: none;
	}
	.book-cover{
		width: 20%;
		/*width: 4.125rem;*/
		float: left;
		margin-right: 0.5rem;
		box-shadow: 0 4px 8px rgba(51,55,61,0.1);
	}
	.book-cell{
		overflow: hidden;
	}
	.book-title{
		line-height: 1.4;
		white-space: nowrap;
		text-overflow: ellipsis;
		overflow: hidden;
		text-align: left;
		color: black;
		font-size: 1rem;
	}
	.book-ol-normal .book-desc{
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 2;
		line-height: 1.1875rem;
	}
	.book-desc{
		margin: 0.2rem 0 0.3rem 0;
		font-size: 0.8125rem;
		color: #808080;
		overflow: hidden;
		text-align: left;
	}
	.book-meta{
		font-size: 0.75rem;
		overflow: hidden;
		line-height: 1.7;
	}
	.book-meta-l{
		float: left;
	}
	.book-meta-r{
		float: right;
		position: relative;
	}
	.book-author{
		display: inline-block;
		color: #808080;
		white-space: nowrap;
		text-overflow: ellipsis;
		font-size: 0.75rem;
		overflow: hidden;
		line-height: 0.75rem;
		margin-left: -3px;
		vertical-align: -0.5ex;
	}
	.tag-small-group{
		position: absolute;
		right: 0;
		display: inline-block;
		white-space: nowrap;
	}
	.tag-small{
		display: inline-block;
		line-height: 1.5;
		padding: 0 0.25em;
		/*margin: 0 0.15em;*/
		vertical-align: bottom;
		border: 1px solid;
		font-size: 0.75rem;
	}
	.yellow{
		color: #ffa100;
		border: 1px solid rgba(255,161,0,0.3);
	}
	.red{
		color: #FF3955;
		border: 1px solid rgba(255,57,85,0.3);
	}
	.blue{
		color: #4284ee;
		border: 1px solid rgba(66,132,238,0.3);
	}
	/*尾部*/
	footer{
		background-color: #FFFFFF;
	}
	.footer-link{
		color: #808080;
		font-size: 0.875rem;
		text-align: center;
		display: -webkit-box;
		justify-content: space-between;
		-webkit-box-pack: justify;
		padding: 0.5625rem 1.1875rem 0;
		border-top: 1px solid #F0F1F2;
	}
	.footer-link-a{
		color: #1A1A1A;
		display: block;
		padding: 0.5rem 0;
		-webkit-box-flex: 1;
	}
	.footer-copy{
		color: #808080;
		font-weight: 300;
		font-size: 0.75rem;
		text-align: center;
		padding-top: 0.25rem;
		padding-bottom: 1rem;
	}
	.footer-backtop-circle{
		position: fixed;
		z-index: 1;
		bottom: 1rem;
		right: 1rem;
		width: 2.75rem;
		height: 2.75rem;
		background-color: rgba(0,0,0,0.6);
		color: #FFFFFF;
		border-radius: 50%;
	}
	.footer-backtop-circle>i{
		display: inline-block;
		transform: rotate(90deg);
		font-size: 1.75rem;
		margin-left: 0.875rem;
		margin-top: 0.43525rem;
		vertical-align: -0.25ex;
	}
	/*搜索页*/
	.search-popup{
		background-color: #FFFFFF;
		position: fixed;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
		z-index: 20;
		visibility: hidden;
	}
	.search-header{
		/*height: 2.75rem;*/
		padding-top: 0.7rem;
		padding-bottom: 0.7rem;
		border-bottom: 1px solid #F0F1F2;
		background-color: #FFFFFF;
		position: relative;
		box-sizing: border-box;
	}
	.search-form{
		overflow: hidden;
	}
	.search-area{
		height: 80%;
		background-color: #F6F7F9;
		border-radius: 0.25rem;
		position: absolute;
		left: 1rem;
		right: 3.75rem;
		top: 0;
		bottom: 0;
		margin: auto;
	}
	.search-area i{
		position: absolute;
		left: 0.5rem;
		top: 0;
		bottom: 0;
		color: #808080;
		margin: auto;
	}
	.search-input{
		width: 100%;
		height: inherit;
		border: 0 none;
		background: none;
		padding: 1.05rem 2rem;
		font-size: 0.875rem;
	}
	.search-cancel{
		float: right;
		margin-right: 1rem;
		color: #FF3955;
		font-size: 0.875rem;
	}
	.search-history{
		overflow: hidden;
	}
	.search-title-bar{
		line-height: 1.8125rem;
		padding: 1rem 1rem 0;
		background-color: rgba(0,0,0,0.03);
		overflow: hidden;
	}
	.search-title{
		font-size: 0.8125rem;
		color: #808080;
		font-weight: 400;
		float: left;
	}
	.search-tags{
		padding: 0.25rem 0.5rem 0.75rem 1rem;
	}
	.btn-line{
		display: inline-block;
		line-height: 1.6875rem;
		border: 1px solid;
		border-radius: 99px;
		padding: 0 0.625rem;
		font-size: 0.8125rem;
		text-align: center;
		margin: 0.5rem 0.5rem 0 0;
		color: #808080;
	}
</style>