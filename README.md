
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8" />
    <title>demo</title>
    <link rel="stylesheet" href="css.css"/>
    <script src="js/animate.js"></script>
</head>
<body>
	<div class="box1" id="box1">
		<div class="box2" id="box2">
			<div class="box3" id="box3">
				<div class="box4" id="box4">
					<img src="images/a15.png" alt=""/>
				</div>
				<div class="box5" id="box5">
					<span id="container" style="margin-left: 0px;">
						<marquee>
						[温馨提示]最近有不少不法分子在网上骗人,请大家注意!!!
					</marquee>
					</span>
				</div>
			</div>
		</div>
		<div class="box" id="box">
			<div class="slider" id="slider">
				<div class="slide"><img src="images/b5.png" alt=""/></div>
				<div class="slide"><img src="images/b1.png" alt=""/></div>
				<div class="slide"><img src="images/b2.png" alt=""/></div>
				<div class="slide"><img src="images/b3.png" alt=""/></div>
				<div class="slide"><img src="images/b4.png" alt=""/></div>
				<div class="slide"><img src="images/b5.png" alt=""/></div>
				<div class="slide"><img src="images/b1.png" alt=""/></div>			
			</div>
			<span id="left"><</span>
			<span id="right">></span>
			<ul class="nav" id="nav">
				<li class="active">1</li>
				<li>2</li>
				<li>3</li>
				<li>4</li>
				<li>5</li>
			</ul>
		</div>
	</div>
</body>
	<script>
		var box = document.getElementById("box");
		var oNavlist = document.getElementById("nav").children;
		var slider = document.getElementById("slider");
		var left = document.getElementById("left");
		var right = document.getElementById("right");
		var index = 1;
		var timer;
		var isMoving = false;
		// 轮播下一张的函数
		function next(){
			index++;
			navChange();
			animate(slider,{left:-1200*index},function(){
				if(index === 6){
					slider.style.left = "-1200px";
					index = 1;
				}
			});	
		}
		// 轮播上一张的函数
		function prev(){
			index--;
			navChange();
			animate(slider,{left:-1200*index},function(){
				if(index === 0){
					slider.style.left = "-6000px";
					index = 5;
				}
			});	
		}
		var timer = setInterval(next, 3000);
		// 鼠标划入清定时器
		box.onmouseover = function(){
			animate(left,{opacity:50});
			animate(right,{opacity:50});
			clearInterval(timer);
		}
		// 鼠标划出开定时器
		box.onmouseout = function(){
			animate(left,{opacity:0});
			animate(right,{opacity:0});
			timer = setInterval(next,3000);
		}
		right.onclick = next;
		left.onclick = prev;
		// 小按钮点击事件
		for(var i=0;i<oNavlist.length;i++){
			oNavlist[i].index = i;
			oNavlist[i].onclick = function(){
				index = this.index + 1;
				animate(slider,{left:-1200*index});
				navChange();
			}
		}
		// 小按钮背景色切换
		function navChange(){
			for(var i=0;i<oNavlist.length;i++){
				oNavlist[i].className = '';
			}
			if(index === 6){
				oNavlist[0].className = 'active';
			}else if(index === 0){
				oNavlist[4].className = 'active';
			}else{
				oNavlist[index-1].className = 'active';
			}
		}		
	</script>
</html>
