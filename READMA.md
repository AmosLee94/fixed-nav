让一个在正常文档流的nav在被滚动到上面，被隐藏起来时，被固定在视窗的顶部

需要用到的代码：
* CSS
>` .fixed-top{position: fixed;top:0;left: 0;right: 0;}
 .hidden{display:none;}`
***
* Javascript
>(function(){
	var nav = document.getElementsByTagName('nav')[0];
	var pseudoNav = document.createElement("div");
	pseudoNav.style.height = nav.clientHeight+'px';
	pseudoNav.className = 'hidden';
	document.body.insertBefore(pseudoNav,nav);
	var y0= nav.getBoundingClientRect().top+document.body.scrollTop;
		window.addEventListener("scroll",function(){
			var y= document.body.scrollTop;
			if(y>=y0){
				nav.className = 'fixed-top';
				pseudoNav.className = 'block';
			}else{
				nav.className = '';
				pseudoNav.className = 'hidden';
			}
		});
})();
***
* HTML
>`导航栏用nav且第一条有效`