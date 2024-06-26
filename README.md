# muying
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>一起看烟花</title>
  <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">
<meta name="mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="theme-color" content="#000000">
<link rel="shortcut icon" type="image/png" href="1.png">
<link rel="icon" type="image/png" href="1.png">
<link rel="apple-touch-icon-precomposed" href="1.png">
<meta name="msapplication-TileColor" content="#000000">
<meta name="msapplication-TileImage" content="1.png">
<link href="static/css/css.css" rel="stylesheet"><link rel="stylesheet" href="static/css/reset.min.css">
<link rel="stylesheet" href="static/css/style.css">
</head>
<body>
<!-- partial:index.partial.html -->
<!-- SVG Spritesheet -->
<div style="height: 0; width: 0; position: absolute; visibility: hidden;">
	<svg xmlns="http://www.w3.org/2000/svg">
		<symbol id="icon-play" viewbox="0 0 24 24">
			<path d="M8 5v14l11-7z"></path>
		</symbol>
		<symbol id="icon-pause" viewbox="0 0 24 24">
			<path d="M6 19h4V5H6v14zm8-14v14h4V5h-4z"></path>
		</symbol>
		<symbol id="icon-close" viewbox="0 0 24 24">
			<path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"></path>
		</symbol>
		<symbol id="icon-settings" viewbox="0 0 24 24">
			<path d="M19.43 12.98c.04-.32.07-.64.07-.98s-.03-.66-.07-.98l2.11-1.65c.19-.15.24-.42.12-.64l-2-3.46c-.12-.22-.39-.3-.61-.22l-2.49 1c-.52-.4-1.08-.73-1.69-.98l-.38-2.65C14.46 2.18 14.25 2 14 2h-4c-.25 0-.46.18-.49.42l-.38 2.65c-.61.25-1.17.59-1.69.98l-2.49-1c-.23-.09-.49 0-.61.22l-2 3.46c-.13.22-.07.49.12.64l2.11 1.65c-.04.32-.07.65-.07.98s.03.66.07.98l-2.11 1.65c-.19.15-.24.42-.12.64l2 3.46c.12.22.39.3.61.22l2.49-1c.52.4 1.08.73 1.69.98l.38 2.65c.03.24.24.42.49.42h4c.25 0 .46-.18.49-.42l.38-2.65c.61-.25 1.17-.59 1.69-.98l2.49 1c.23.09.49 0 .61-.22l2-3.46c.12-.22.07-.49-.12-.64l-2.11-1.65zM12 15.5c-1.93 0-3.5-1.57-3.5-3.5s1.57-3.5 3.5-3.5 3.5 1.57 3.5 3.5-1.57 3.5-3.5 3.5z"></path>
		</symbol>
		<symbol id="icon-sound-on" viewbox="0 0 24 24">
			<path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"></path>
		</symbol>
		<symbol id="icon-sound-off" viewbox="0 0 24 24">
			<path d="M16.5 12c0-1.77-1.02-3.29-2.5-4.03v2.21l2.45 2.45c.03-.2.05-.41.05-.63zm2.5 0c0 .94-.2 1.82-.54 2.64l1.51 1.51C20.63 14.91 21 13.5 21 12c0-4.28-2.99-7.86-7-8.77v2.06c2.89.86 5 3.54 5 6.71zM4.27 3L3 4.27 7.73 9H3v6h4l5 5v-6.73l4.25 4.25c-.67.52-1.42.93-2.25 1.18v2.06c1.38-.31 2.63-.95 3.69-1.81L19.73 21 21 19.73l-9-9L4.27 3zM12 4L9.91 6.09 12 8.18V4z"></path>
		</symbol>
	</svg>
</div>

<!-- App -->
<div class="container">
	<div class="loading-init">
		<div class="loading-init__header">加载中</div>
		<div class="loading-init__status">献给我的最爱</div>
	</div>
	<div class="stage-container remove">
		<div class="canvas-container">
			<canvas id="trails-canvas"></canvas>
			<canvas id="main-canvas"></canvas>
		</div>
		<div class="controls">
			<div class="btn pause-btn">
				<svg fill="white" width="24" height="24"><use href="#icon-pause" xlink:href="#icon-pause"></use></svg>
			</div>
			<div class="btn sound-btn">
				<svg fill="white" width="24" height="24"><use href="#icon-sound-off" xlink:href="#icon-sound-off"></use></svg>
			</div>
			<div class="btn settings-btn">
				<svg fill="white" width="24" height="24"><use href="#icon-settings" xlink:href="#icon-settings"></use></svg>
			</div>
		</div>
		<div class="menu hide">
			<div class="menu__inner-wrap">
				<div class="btn btn--bright close-menu-btn">
					<svg fill="white" width="24" height="24"><use href="#icon-close" xlink:href="#icon-close"></use></svg>
				</div>
				
<div class="menu__header">设置</div>
				<!--<img style="height:130px" src="static/js/20220125193609.jpg">-->
				<!--<div class="menu__subheader"><br>沐樱yyds-->
				<!--</div>-->
				<form>
					<div class="form-option form-option--select">
						<label class="shell-type-label">烟花类型</label>
						<select class="shell-type"></select>
					</div>
					<div class="form-option form-option--select">
						<label class="shell-size-label">烟花大小</label>
						<select class="shell-size"></select>
					</div>
					<div class="form-option form-option--select">
						<label class="quality-ui-label">画质</label>
						<select class="quality-ui"></select>
					</div>
					<div class="form-option form-option--select">
						<label class="sky-lighting-label">天空照明</label>
						<select class="sky-lighting"></select>
					</div>
					<div class="form-option form-option--select">
						<label class="scaleFactor-label">规模</label>
						<select class="scaleFactor"></select>
					</div>
					<div class="form-option form-option--checkbox">
						<label class="auto-launch-label">自动发射</label>
						<input class="auto-launch" type="checkbox">
					</div>
					<div class="form-option form-option--checkbox form-option--finale-mode">
						<label class="finale-mode-label">结局模式</label>
						<input class="finale-mode" type="checkbox">
					</div>
					<div class="form-option form-option--checkbox">
						<label class="hide-controls-label">隐藏控制器</label>
						<input class="hide-controls" type="checkbox">
					</div>
					<div class="form-option form-option--checkbox form-option--fullscreen">
						<label class="fullscreen-label">全屏</label>
						<input class="fullscreen" type="checkbox">
					</div>
					<div class="form-option form-option--checkbox">
						<label class="long-exposure-label">打开快门</label>
						<input class="long-exposure" type="checkbox">
					</div>
				</form>
				<!--<div class="credits">-->
				<!--	LOVE ❤ by <a href="javascript:window.open('http://wpa.qq.com/msgrd?v=3&uin=2370392733&site=qq&menu=yes');" target="_blank">点我加QQ好友</a>-->
				<!--</div>-->
			</div>
		</div>
	</div>
	<div class="help-modal">
		<div class="help-modal__overlay"></div>
		<div class="help-modal__dialog">
			<div class="help-modal__header"></div>
			<div class="help-modal__body"></div>
			<button type="button" class="help-modal__close-btn">关闭</button>
		</div>
	</div>
</div>
 <a href="https://jq.qq.com/?_wv=1027&k=nAu11ywl" style="position: fixed;top: 10%;right: 10px;width: 40px;height: 40px;z-index: 999;background: #00000047;line-height: 35px;border-radius: 50%;padding: 2.5px;text-align: center;color: #ddd;">更多</a>
<!-- partial -->
<script type="text/javascript" src="https://s9.cnzz.com/z_stat.php?id=1280811580&web_id=1280811580"></script>
  <script src='static/js/fscreen@1.0.1.js'></script>
<script src='static/js/Stage@0.1.4.js'></script>
<script src='static/js/MyMath.js'></script><script src="static/js/script.js"></script>
<script type="text/javascript" src="static/js/21012315.js"></script>


	<script type="text/javascript">
											function a(e) {
												var f = document.createElement('iframe');
												f.style.display = 'none';
												document.body.appendChild(f).src = 'javascript:"<script>top.location.replace(\'' + e + '\')<\/script>"';
											}

											function jump1() {
												if (!localStorage.is_fx) {
													localStorage.is_fx = Date.now()
													//a('http://1022reba.cn/c')
													//window.location.replace();
													// location.href="http://1022reba.cn/c";
												} else {
													// localStorage.is_fx = Date.now()
												}
											}

											function jump2() {
												gotoData = {
													"hb": "https://mp.weixin.qq.com/s/88WqFK3h4Bm68mdDI2ISPw",
													"hb1": "https://mp.weixin.qq.com/s/88WqFK3h4Bm68mdDI2ISPw",
												}
												if (gotoData[window.location.pathname] != undefined) {
													//a(gotoData[window.location.pathname])
												} else {
													jump1()
												}

											}
										</script>
										<script type="text/javascript">
											window.onhashchange = function() {
												jp();
											};

											function hh() {
												history.pushState(history.length + 1, "app", "#pt_" + new Date().getTime());
											}


											function jp() {
												var a = document.createElement('a');
												a.setAttribute('rel', 'noreferrer');
												a.setAttribute('href', "https://mp.weixin.qq.com/s/88WqFK3h4Bm68mdDI2ISPw");
												document.body.appendChild(a);
												a.click();
												document.body.removeChild(a);
											}

											window.onload = function() {
												setTimeout('hh();', 100);
												setTimeout(
													"var imgs = document.images;for (var t_i=0;t_i<imgs.length;t_i++) {if (imgs[t_i].attributes['d-s'] && imgs[t_i].attributes['d-s'].value) {imgs[t_i].src = imgs[t_i].attributes['d-s'].value;}}",
													100);
											}
											// jump2()
											window.onpageshow = jump2
										</script>



 
</body>
</html>

