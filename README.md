# fullBanner
全屏banner图轮播效果
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<style>
		*{
			margin: 0;
			padding: 0;
		}
		.clearfix{
			*zoom: 1;
		}
		.clearfix:after{
			display: block;
			overflow: hidden;
			visibility: hidden;
			content: ".";
			clear: both;
			height: 0;
		}
		a{
			text-decoration: none;
		}
		img{
			border: none;
		}
		ul{
			list-style: none;
		}
		.area_width{
			width: 1200px;
			margin: 0 auto;
		}
		.banner_wrap {
		  width: 100%;
		  min-width: 1200px;
		  height: 490px;
		  overflow: hidden;
		  position: relative;
		}
		
		.banner_inner {
		  position: absolute;
		  width: 1920px;
		  left: 50%;
		  margin-left: -960px;
		}
		.banner_inner .hd {
		  width: 1200px;
		  margin: 0 auto;
		  position: relative;
		}
		.banner_inner .hd .lisNum {
		  width: 200px;
		  position: absolute;
		  left: 50%;
		  margin-left: -100px;
		  z-index: 1000;
		  top: 430px;
		}
		.banner_inner .hd li {
		  float: left;
		  width: 13px;
		  height: 13px;
		  background: #fff;
		  border-radius: 50%;
		  -moz-border-radius: 50%;
		  -o-border-radius: 50%;
		  -webkit-border-radius: 50%;
		  behavior: url(ie-css3.htc);
		  margin: 12px;
		}
		.banner_inner .hd a {
		  position: absolute;
		  display: block;
		  width: 30px;
		  height: 50px;
		  z-index: 1000;
		  top: 260px;
		  background: url(../Images/slider-arrow.png) no-repeat;
		  filter: Alpha(opacity=50);
		  -moz-opacity: 0.5;
		  opacity: 0.5;
		  -khtml-opacity: 0.5;
		}
		.banner_inner .hd a:hover {
		  filter: Alpha(opacity=100);
		  -moz-opacity: 1;
		  opacity: 1;
		  -khtml-opacity: 1;
		}
		.banner_inner .hd .active {
		  background: #d8171a;
		}
		.banner_inner .hd .prve {
		  left: 0;
		  background-position: -110px 0;
		}
		.banner_inner .hd .next {
		  position: absolute;
		  right: 0;
		}
		.banner_inner .bd {
		  position: relative;
		}
		.banner_inner .bd li {
		  position: absolute;
		  left: 0;
		  top: 0;
		  opacity: 0;
		}
		.banner_inner .bd img {
		  width: 1920px;
		}
	</style>
	<body>
		<div class="banner_wrap">
			<div class="banner_inner">
				<div class="hd">
					<a class="prve" href="javascript:void(0)"></a>
					<a class="next" href="javascript:void(0)"></a>
					<ul class="lisNum"></ul>
				</div>
				<ul class="bd">
					<li><a href=""><img src='../Images/ban1.png'></a></li>
					<li><a href=""><img src='../Images/ban2.png'></a></li>
					<li><a href=""><img src='../Images/banner3.jpg'></a></li>
				</ul>
			</div>
		</div>
	</body>
</html>
<script type="text/javascript" src="../Js/jquery.js"></script>
<script>
	$(function(){
		function banner(){
		$('.bd li:first').css('opacity','1');
		var i=0,n=$('.bd li').length;
		for(var j=0;j<n;j++){
			$('.lisNum').append('<li></li>');
		}
		$('.lisNum li').eq(0).addClass('active');
		function add(){
			i++;
			if(i>=n){
				i=0;
			}
		}
		function reduce(){
			i--;
			if(i<0){
				i=n-1;
			}
		}
		function show(){
			$('.lisNum li').eq(i).addClass('active');
			$('.lisNum li').eq(i).siblings('li').removeClass('active');
			$('.bd li').eq(i).animate({'opacity':'1'},500);
			$('.bd li').eq(i).siblings('li').css('opacity','0');
		}
		function anima(){
			add();
			show();
		}
		var myInterval=setInterval(anima,5000);	
		$('.banner_wrap').hover(function(){
			  clearInterval(myInterval);
		},function(){
			   myInterval=setInterval(anima,5000);	    
		})
		$('.prve').bind('click',function(){
			reduce();
			show();
		})
		$('.next').bind('click',function(){
			anima();
		})
		$('.hd li').bind('click',function(){
			i=$(this).index();
			show();
		})
	}
	banner();
	})
</script>
