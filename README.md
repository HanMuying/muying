# muying
<!DOCTYPE html>  
<html lang="en">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>沐樱|文字转语音</title>
	<style>  
	    body {  
	        background-image: url('123.jpg');  
	        /* 其他可选的样式属性，如背景大小、位置等 */  
	        background-size: cover; /* 这将使背景图片覆盖整个元素 */  
	        background-position: center; /* 这将使背景图片在元素中居中 */  
	        background-repeat: no-repeat; /* 这将防止背景图片重复 */  
	    }  
		 #textToSpeak {  
		        /* 设置背景颜色，并使用 rgba 来添加透明度 */  
		        background-color: rgba(255, 255, 255, 0.5); /* 白色半透明，透明度为 0.5 */  
		        /* 你可以根据需要调整颜色和透明度值 */  
		  
		        /* 其他可能的样式 */  
		        border: 1px solid #ccc; /* 边框 */  
		        padding: 10px; /* 内边距 */  
		        resize: vertical; /* 允许垂直调整大小 */  
		    }
			  .speak-button {  
			              background-color: #4CAF50; /* 背景色 */  
			              color: white; /* 字体颜色 */  
			              padding: 10px 100px; /* 内边距 */  
			              border: none; /* 边框 */  
			              border-radius: 4px; /* 圆角 */  
			              cursor: pointer; /* 鼠标悬停时显示为小手 */  
			          }  
	</style>
	<link rel="icon" href="img/kk.png">
</head>  
<body>  
  
<textarea id="textToSpeak" rows="50" cols="200">  
    请在此处输入您想要转换为语音的文本。  
</textarea>  
  
 <button onclick="speak()" class="speak-button">开始朗读</button>  
  
<script>  
    function speak() {  
        // 获取文本  
        const text = document.getElementById('textToSpeak').value;  
  
        // 创建一个新的 SpeechSynthesisUtterance 实例  
        const utterance = new SpeechSynthesisUtterance(text);  
  
        // 设置语音的音量、语速等（可选）  
        utterance.volume = 1; // 0 到 1 之间  
        utterance.rate = 1; // 默认语速为 1，可以是 0.1 到 10 之间的任何值  
        utterance.pitch = 1; // 0 到 2 之间的值，默认为 1  
  
        // 尝试选择一个可用的语音  
        // 注意：这取决于用户的浏览器和系统配置，可能不可用或非常有限  
        const voices = window.speechSynthesis.getVoices();  
        // 查找特定语言或名称的语音（例如，英文的 "Google UK English Female"）  
        // 这里只是一个示例，实际上你可能需要遍历 voices 数组来找到合适的语音  
        for (let i = 0; i < voices.length; i++) {  
            if (voices[i].lang === 'en-US' && voices[i].name === 'Google US English') {  
                utterance.voice = voices[i];  
                break;  
            }  
        }  
  
        // 如果未找到特定语音，则使用默认语音  
        if (!utterance.voice) {  
            console.log('No matching voice found, using default.');  
        }  
  
        // 开始朗读  
        window.speechSynthesis.speak(utterance);  
    }  
  
    // 监听 voiceschanged 事件，以便在可用语音改变时更新选项（如果有的话）  
    window.speechSynthesis.onvoiceschanged = function() {  
        const voices = window.speechSynthesis.getVoices();  
        // 在这里可以更新用户界面以显示可用的语音选项（如果有的话）  
    };  
</script>  
  
</body>  
</html>
