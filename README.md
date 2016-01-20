# sharejs
`sharejs` 是微信分享的前端组件，它可以快速对接后端的微信分享逻辑，并在不同页面传入不同的 `option` 即可分别分享不同的内容。
## Basic Usage
1. 引入微信分享接口和`sharejs`到你的页面中
	
    ```html
    <script type="text/javascript" src="http://res.wx.qq.com/open/js/jweixin-1.0.0.js"></script>
	<script type="text/javascript" src="share.js"></script>
    ```

2. 修改`sharejs`中的配置对象`initConfig`，initConfig详细说明见下文API处

3. 执行`share()`方法并传入`option`，option详细说明见下文API处

    ```javascript
    share({
		title: 'string',
		desc: 'string',
		shareUrl: 'string',
		imgUrl: 'string',
		goToUrl: 'string',
		from: 'string'
	});
    ```

4. 现在你可以在微信中分享你的页面了

## API

### initConfig配置说明

initConfig例子：
```javascript
var initConfig = {
    getConfigPath : '/wxShareAjax',
    defaultImgUrl : 'weixindefault.jpg',
    secondObject : 'msg',
    appIdKey : 'appId',
    timestampKey : 'timestamp',
    nonceStrKey : 'noncestr',
    signatureKey : 'signature',
};
```

服务器返回的json例子：
```json
{"error":0,"msg":{"signature":"123qwe123qwe","noncestr":"abc","timestamp":1453279155,"appId":"wxxxxxx","url":"http:\/\/xxx.com"}}
```

* getConfigPath 必填，string，获取微信分享各个参数的后端AJAX接口路径，例如：'/wxShareAjax'
* defaultImgUrl 必填，string，分享的图标缺省时，显示的缺省图标url，例如：'weixindefault.jpg'
* secondObject 选填，string，后端返回的json数据，若在二级属性中，则在此填二级属性名，若在一级则不填。若如上述json所示，则此处填写'msg'
* appIdKey：必填，string，返回json中appid的键名。若如上述json所示，则此处填写'appId'
* timestampKey：必填，string，返回json中时间戳的键名。若如上述json所示，则此处填写'timestamp'
* nonceStrKey：必填，string，返回json中随机字符串的键名。若如上述json所示，则此处填写'noncestr'
* signatureKey：必填，string，返回json中签名的键名。若如上述json所示，则此处填写'signature'

### option配置说明

option例子：
```javascript
share({
	title: 'string',
	desc: 'string',
	shareUrl: 'string',
	imgUrl: 'string',
	goToUrl: 'string',
	from: 'string'
});
```
* title 必填，string，分享的标题
* desc 必填，string，分享的描述
* shareUrl 选填，string，分享的链接，若不填则分享当前页
* imgUrl 选填，string，分享的图标链接，若不填则显示缺省图标
* goToUrl 选填，string，分享成功后跳转到的链接
* from 选填，string，分享成功后计数的ajax链接，每次成功分享都会请求一次此ajax接口
