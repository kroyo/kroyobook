# 原生ajax



```javascript 
function send_request() {  
    var xmlhttp = null;  
    if(window.XMLHttpRequest)  
    {
        xmlhttp = new XMLHttpRequest();
    } else if(window.ActiveXObject)
    {
    	// IE5,IE6
        xmlhttp = new ActiveXObject("Microsoft.XMLHTTP");
    }

    if(xmlhttp != null)
    {
    	xmlhttp.onreadystatechange = function () { // 状态发生变化时，函数被回调
		    if (request.readyState === 4) { // 成功完成
		        // 判断响应结果:
		        if (request.status === 200) {
		            // 成功，通过responseText拿到响应的文本:
		            return success(request.responseText);
		        } else {
		            // 失败，根据响应码判断失败原因:
		            return fail(request.status);
		        }
		    } else {
		        // HTTP请求还在继续...
		    }
		}
        serverUrl = 'http://api.storage.laisj.com/get.php';
        xmlhttp.open( "GET", serverUrl, false );
        xmlhttp.send( null );
        return xmlhttp.responseText
    } else {
        alert("Your browser does not support XMLHTTP.");
    }  
};
```