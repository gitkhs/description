## 크로스사이트 도메인 AJAX

### HTTP Request
ajax 요청시 **withCredentials**값 설정 하며
**contentType** 은 `application/x-www-form-urlencoded`, `multipart/form-data`, `text/plain` 을 사용한다.
```
POST /cors HTTP/1.1
Origin: http://reuqest.com
Host: xxx.com
```

### HTTP Response
크로스사이트 도메인 값을 `Access-Control-Allow-Origin:*`으로 전체로 할경우 ajax에 대한 응답을 내려 주지만
세션 유지가 도지 않은 요청한 도메인의 값을 같이 세팅 해줘야 된다.
```
Access-Control-Allow-Origin: http://reuqest.com
Access-Control-Allow-Credentials: true
```


### Javascript
```javascript
var xhr = new XMLHttpRequest();
if ("withCredentials" in xhr) {
	xhr.open(method, url, true);
} else if (typeof XDomainRequest != "undefined") {
	xhr = new XDomainRequest();
    xhr.open(method, url);
}
```

### Jquery
```javascript
$.ajax({
	contentType: "application/x-www-form-urlencoded; charset=utf-8",
	xhrFields: {
		withCredentials: true
	}
})
```

### Java
```java
HttpServletRequest request = (HttpServletRequest) req;
response.setHeader("Access-Control-Allow-Origin", request.getHeader("Origin"));
response.setHeader("Access-Control-Allow-Credentials","true");
```

### PHP
```php
$hd = apache_request_headers();
header('Content-Type: application/json');
if(isset($hd['origin'])) {
	header('Access-Control-Allow-Origin: '.$hd['origin']);
	header('Access-Control-Allow-Credentials: true');
}
```

### 참고자료
[Using CORS](https://www.html5rocks.com/en/tutorials/cors/?redirect_from_locale=ko)

[cross domain ajax call](http://paulina0206.tistory.com/m/entry/cross-domain-ajax-call-%ED%95%A0-%EB%95%8C-JSESSIONID-%EC%BF%A0%ED%82%A4%EA%B0%92-%EC%A0%84%EC%86%A1%ED%95%98%EA%B8%B0)