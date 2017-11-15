#### 封装JSONP
```javascript
  function jsonp(url, value, Callback) {
    var hasParams = url.indexOf('?');
    url += hasParams ? '&' : '?' + value +'callback=' + Callback;
    var oScript = document.createElement('script')
    oScript.setAttribute('src', url)
    document.body.appendChild(oScript);
  }
    function Callback(data) {
    console.log(data)
  }
```
<br>

#### JSONP优点
    1.不受同源策略限制，可以跨域
    2.兼容性好，不需要XHR或ActiveX的支持
    3.请求完毕后可通过调用callback方法回传结果
<br>

#### JSONP缺点
    1.只支持get请求，不支持post等其他类型请求
    2.之至此跨域HTTP请求，不能解决不同域的两个页面之间的js调用
    3.JSONP调用失败不返回HTTP状态码
    4.安全性较差，使用JSONP时必须要保证JSONP服务室安全可信的