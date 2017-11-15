* AJAX是Asynchronous javascript and xml 的缩写，用javascript以异步的形式操作xml(现在操作的是json)
#### AJAX优点
    1.页面无刷新，在页面内与服务器通信，给用户的体验很好。
    2.使用异步的形式与服务器进行通信，不需要打断用户的操作，给用户的体验更好。
    3.减轻服务器的负担。
    4.不需要插件或者小程序。
<br>

#### AJAX缺点
    1.不支持浏览器的后退机制。
    2.安全问题，跨站点脚本攻击、sqi注入攻击。
    3.对搜索引擎支持较弱（seo）。
    4.不支持移动设备。
    5.违背了url和资源定位的初衷。
<br>

#### AJAX涉及到的两个知识点：
##### readyState（对象的状态）
    - 值　　常量　　　　　　　　　 含义
    - 0　　UNSEND　　　　　　　　open()未调用
    - 1　　OPENED　　　　　　　　open()已调用
    - 2　　HEADERS_RECEIVED　　接收到头信息
    - 3　　LOADING　　　　　　　接收到响应主体
    - 4　　DONE　　　　　　　　　响应完成
<br>

##### status（信息状态码）
###### 1xx（信息性状态码）
###### 2xx（成功状态码）
    - 200 OK 请求已经被服务器正常处理。
    - 204 No Content 请求处理成功，但是没有资源可以返回。
###### 3xx（重定向状态码）
    - 301 Moved Permanently 永久性重定向
    - 302 Found 临时性重定向，禁止post变成get
    - 303 See Other 请求的对应资源存在着另一个URI，因使用GET方法定性获取请求的资源
    - 304 Not Modified 资源已找到，但是没有被修改过，不符合要求
    - 307 Temporary Redirect 临时重定向，与302含义相同
###### 4xx（客户端错误状态码）
    - 400 Bad Request 请求报文中存在语法错误
    - 401 Unauthorized 发送的请求需要通过HTTP的认证信息。如果之前请求过认证失败。
    - 403 Forbidden 不允许访问该资源
    - 404 Not Found 服务器上没有改资源
###### 5xx（服务器错误状态码）
    - 500 Internal Server Error 服务器端在执行请求时发生错误
    - 503 Service Unavailable 服务器暂时处于超载或正在停机维护
<br>

#### AJAX流程
    1.生成一个ajax对象
    2.调用open（method，url，flag）方法
    3.通过send提交数据
    4.监听状态改变，当数据请求成功之后调用回调函数
<br>

### 封装AJAX
```javascript
 function AJAX(json) {
	var url = json.url,
		method = json.method,
		flag = json.flag,
		data = json.data,
		callBack = json.callBack,
		xhr = null;
	if(window.XMLHttpRequest) {
		xhr = new window.XMLHttpRequest();
	}else {
		xhr = new ActiveXObject('Mircosoft.XMLHTTP');
	}			
	if(method == 'get') {
                url += '?' + data + new Date().getTime(); 
		xhr.open('get', url, flag);
	}else {
		xhr.open('post', url, flag);
	}
	xhr.onreadystatechange = function () {
		if (xhr.readyState === 4 && xhr.status === 200) {
			callBack(xhr.responseText);
		}
	}
	if(method == 'get') {
		xhr.send();
	}else {
		xhr.setRequestHeader('Content-Type', 'application/x-www-form-urle');
		xhr.send(data);
	}	
}
```