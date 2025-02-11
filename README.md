# ChatGPT-ToolBox

由ChatGPT负责编写的ChatGPT工具箱。除了向ChatGPT提供必要的数据，尽可能不由人类写任何代码。


当前版本提供以下功能：

1.关闭数据监管

2.会话导入导出

3.高负载限制解锁：

  .强制启用「Regenerate Response」

  .禁止登录时，解锁登录界面




![oofReplaceGif](https://user-images.githubusercontent.com/3683548/212370351-92382e56-a28d-41ac-b170-d600f9a5aa09.gif)

(↑GIF如果无法正常播放请点击查看原图↑)


# 预览：

![image](https://user-images.githubusercontent.com/3683548/208979114-66271013-ec57-4425-9502-661236b99aaa.png)


# 🔄更新

2023-1-13

. 新增oof强制覆盖。现在，脚本加载时可以解除高负载状态的限制。例如「Regenerate Response」的禁用状态，或是登录页的高负载禁止登录。


2022-12-22

. 官方会话管理器已正式推送，移除第三方会话管理器

. 修复会话导入导出

. 会话导入现在又可以导入他人的会话了(依然受token存活影响)


2022-12-16

~~. 增加存档管理~~ (官方会话管理已正式推送)

. 增加了带记忆的独立监管开关


2022-12-14

. 增加移动端nav覆盖，现在移动端竖屏可以正常使用导航栏

. 修改README里的相关书签链接，提供远端加载最新脚本的书签



# ⚠️ 警告 ⚠️
1 . 导出的会话存档带有鉴权信息，不要分享给不认识的人，否则可能引起账户滥用

2 . 本项目为实验性项目.仅用于探索ChatGPT能力的可能性，请勿长期使用或滥用

3 . 导出的存档在鉴权过期时将会一起失效,请周知。




# 调教过程
↓移步知乎查看图文完整过程

https://zhuanlan.zhihu.com/p/591003498



# 使用方法

## 脚本管理器
您可以考虑使用以下用户搬运发布的UserScript:

·由[@Miller-du](https://github.com/Miller-du)发布的完整加载脚本:

🔗[456901-ChatGPT功能增强](https://greasyfork.org/zh-CN/scripts/456901-chatgpt%E5%8A%9F%E8%83%BD%E5%A2%9E%E5%BC%BA)
 
 
 
·由[@Haorwen](https://github.com/Haorwen)发布的动态加载脚本:

🔗[459199-chatgpt-toolbox](https://greasyfork.org/zh-CN/scripts/459199-chatgpt-toolbox)


*注意：您需要先安装任意一种用户脚本(UserScript)管理器插件(例如TamperMonkey等)，才能通过链接安装它


## PC/MAC Chrome
如果您不想安装任何插件，且您的浏览器是chrome,
请复制对应版本的JS全文，在浏览器里添加一个javascript:开头的脚本书签即可。

1 . 复制以下代码

↓ ↓ 这段JS将会从仓库拉取最新版本的代码并且运行,但需要一点加载时间
```
javascript:var xhr=new XMLHttpRequest();xhr.open('GET','https://ghproxy.com/https://raw.githubusercontent.com/bigemon/ChatGPT-ToolBox/main/toolbox-chrome-bookmark.js',true);xhr.onload=function(){if(xhr.readyState===4&&xhr.status===200){eval(xhr.responseText)}};xhr.send(null);
```


↓↓ 当然,你也可以直接把下面这个完整JS保存到你的书签里运行。
这不需要任何加载时间，但有时候需要手动更新版本
```
javascript:var pageSource=document.documentElement.outerHTML;-1!==pageSource.indexOf('cf-spinner-please-wait')||window.oofPatch||(window.oofPatch=!0,pageSource=pageSource.replace(/\"oof\":true/g,'"oof":false'),document.open(),document.write(pageSource),document.close()),window.enableFakeMod='false'!=localStorage.getItem('enable_fakemod');var style=document.createElement('style');style.innerHTML='.switch{position:relative;display:inline-block;width:60px;height:34px;}.switch input{opacity:0;width:0;height:0;}.slider{position:absolute;cursor:pointer;top:0;left:0;right:0;bottom:0;background-color:#ccc;-webkit-transition:.4s;transition:.4s;}.slider:before{position:absolute;content:"";height:26px;width:26px;left:4px;bottom:4px;background-color:white;-webkit-transition:.4s;transition:.4s;}input:checked + .slider{background-color:#2196F3;}input:focus + .slider{box-shadow:0 0 1px #2196F3;}input:checked + .slider:before{-webkit-transform:translateX(26px);-ms-transform:translateX(26px);transform:translateX(26px);}.slider.round{border-radius:34px;}.slider.round:before{border-radius:50%;}',document.head.appendChild(style),window.switchEnableFakeMod=function(){var a=document.querySelector('input#cswitch'),b=!!a&&a.checked;b?(window.enableFakeMod=!0,localStorage.setItem('enable_fakemod',!0)):(window.enableFakeMod=!1,localStorage.setItem('enable_fakemod',!1))},window.clearAllBoxItem=function(){for(var c,a=document.querySelectorAll('nav'),b=0;b<a.length;b++){c=a[b].querySelectorAll('div.toolbox-item');for(var d=0;d<c.length;d++)c[d].remove()}},window.exportSaveData=function(){var a=window.conversation_id_last||'',b=window.parent_message_id_last||'',c=window.authorization_last;if(''==a||''==b||'undefined'==a||'undefined'==b)return void alert('\u8BF7\u81F3\u5C11\u8BF4\u4E24\u53E5\u8BDD\u518D\u4F7F\u7528\u8FD9\u4E2A\u529F\u80FD!');var e=JSON.stringify({conversation_id:a,parent_message_id:b,authorization:c}),f=window.btoa(e);return f},window.importSaveData=function(a){var b=window.atob(a),c=JSON.parse(b);if(!c||void 0===c.conversation_id||void 0===c.parent_message_id)return void alert('\u4F1A\u8BDD\u5B58\u6863\u5DF2\u635F\u574F, \u8BF7\u786E\u4FDD\u5B8C\u6574\u590D\u5236!');var d=window.getAuthTimestamp(c.authorization)||0;if(!(d&&Math.floor(Date.now()/1e3)>d))alert('\u8FD9\u4E2A\u4F1A\u8BDD\u5B58\u6863\u7684\u6709\u6548\u671F\u6700\u957F\u81F3\uFF1A\r\n'+new Date(1e3*d).toLocaleString('en-US')+'\r\n\r\n\u8BF7\u6CE8\u610F:\u5BFC\u5165\u7684\u4F1A\u8BDD\u65E0\u6CD5\u88AB\u518D\u6B21\u5BFC\u51FA\uFF0C\u4E5F\u65E0\u6CD5\u4FDD\u5B58'),window.import_authorization=c.authorization;else if(!confirm('\u8FD9\u4E2A\u4F1A\u8BDD\u5B58\u6863\u7684Token\u770B\u8D77\u6765\u5DF2\u8FC7\u671F\uFF0C\u6216\u8BB8\u65E0\u6CD5\u6B63\u5E38\u5DE5\u4F5C\u3002\r\n\u5047\u5982\u8FD9\u4E2A\u5B58\u6863\u662F\u7531\u5F53\u524D\u8D26\u53F7\u6240\u5BFC\u51FA\uFF0C\u60A8\u53EF\u4EE5\u5C1D\u8BD5\u4F7F\u7528\u5F53\u524D\u4F1A\u8BDD\u8986\u76D6\u5BFC\u5165\u7684\u72B6\u6001\u3002\r\n\u662F\u5426\u7EE7\u7EED\uFF1F'))return;window.next_conversation_id=c.conversation_id,window.next_parent_message_id=c.parent_message_id,alert('\u5BFC\u5165\u6210\u529F,\u5F53\u524D\u4F1A\u8BDD\u72B6\u6001\u5DF2\u300C\u6682\u65F6\u300D\u9644\u52A0\u5230\u5BFC\u5165\u7684\u5B58\u6863\u3002\u8FD9\u5C06\u5BF9\u60A8\u7684\u4E0B\u4E00\u53E5\u8BDD\u751F\u6548\u3002\r\n\u5982\u679C\u8BE5\u5B58\u6863\u7684\u5BBF\u4E3B\u5DF2\u9000\u51FA\u767B\u5F55\u6216\u91CA\u653E\u8BE5\u4F1A\u8BDD\uFF0C\u5219\u5B58\u6863\u4E5F\u4F1A\u4E00\u8D77\u5931\u6548\r\n\u6B64\u65F6\u60A8\u53EF\u80FD\u4F1A\u88AB\u63D0\u793A\u767B\u5F55\u8FC7\u671F\u3002\r\n\r\n\u82E5\u8981\u4E2D\u9014\u89E3\u9664\u9644\u52A0\u72B6\u6001\u3002\u8BF7\u5237\u65B0\u6D4F\u89C8\u5668\u3001\u70B9\u51FB\u300C +New chat \u300D\u65B0\u5EFA\u4F1A\u8BDD\u6216\u5207\u6362\u5230\u5176\u5B83\u7684\u4F1A\u8BDD\u3002')},window.clearTempValues=function(){delete window.import_authorization,delete window.next_parent_message_id,delete window.next_conversation_id,delete window.parent_message_id_last,delete window.conversation_id_last,delete window.authorization_last},window.boxInit=function(){window.clearAllBoxItem();for(var a=document.querySelectorAll('nav'),b=function _loop(){var e=a[c],f=document.createElement('div'),g=e.querySelectorAll('a');e.childNodes[0].hasOwnProperty('patched')||(e.childNodes[0].addEventListener('click',function(l){l.preventDefault(),confirm('\u5373\u5C06\u521B\u5EFA\u65B0\u7684\u4F1A\u8BDD, \u4F7F\u7528\u5BFC\u5165\u529F\u80FD\u5BFC\u5165\u7684\u4F1A\u8BDD\u5C06\u5931\u6548,\u662F\u5426\u7EE7\u7EED?')&&(e.childNodes[0].removeEventListener('click',arguments.callee),window.clearTempValues(),e.childNodes[0].click())}),Object.defineProperty(e.childNodes[0],'patched',{value:!0,enumerable:!1})),f.setAttribute('class','toolbox-item flex py-3 px-3 items-center gap-3 rounded-md hover:bg-gray-500/10 transition-colors duration-200 text-white cursor-pointer text-sm flex-shrink-0 border border-white/20'),f.innerHTML='<svg t="1670527970700" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="9830" width="18" height="18"><path d="M514 114.3c-219.9 0-398.8 178.9-398.8 398.8 0 220 178.9 398.9 398.8 398.9s398.8-178.9 398.8-398.8S733.9 114.3 514 114.3z m0 685.2c-42 0-76.1-34.1-76.1-76.1 0-42 34.1-76.1 76.1-76.1 42 0 76.1 34.1 76.1 76.1 0 42.1-34.1 76.1-76.1 76.1z m0-193.8c-50.7 0-91.4-237-91.4-287.4 0-50.5 41-91.4 91.5-91.4s91.4 40.9 91.4 91.4c-0.1 50.4-40.8 287.4-91.5 287.4z" p-id="9831" fill="#dbdbdb"></path></svg>\u7981\u7528\u6570\u636E\u76D1\u7BA1<label class="switch" style="position: absolute; right: 15px;"><input id="cswitch" type="checkbox" '+(window.enableFakeMod?'checked=\'true\'':'')+' onclick="window.switchEnableFakeMod()" ><span class="slider"></span></label>',e.insertBefore(f,e.childNodes[1]);var h=document.createElement('div');h.setAttribute('class','toolbox-item flex py-3 px-3 items-center gap-3 rounded-md hover:bg-gray-500/10 transition-colors duration-200 text-white cursor-pointer text-sm flex-shrink-0 border border-white/20'),h.innerHTML='\n        <button id="exportSession" class="btn flex justify-center gap-2 btn-dark btn-small m-auto mb-2">\n            <svg t="1670527911492" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="8753" width="16" height="16"><path d="M562.996016 643.229748V72.074369a50.996016 50.996016 0 0 0-101.992032 0v571.155379a50.996016 50.996016 0 0 0 101.992032 0z" fill="#dbdbdb" p-id="8754"></path><path d="M513.087915 144.080744L802.337317 432.446215a50.996016 50.996016 0 0 0 71.93838-72.210358L513.087915 0 149.588313 362.411687A50.996016 50.996016 0 0 0 221.594688 434.486056L513.087915 144.148738zM53.035857 643.229748v184.537583c0 109.471448 105.255777 192.832935 230.026029 192.832935h457.876228c124.770252 0 230.026029-83.361487 230.026029-192.832935V643.229748a50.996016 50.996016 0 1 0-101.992031 0v184.537583c0 47.256308-55.075697 90.840903-128.033998 90.840903H283.061886c-72.9583 0-128.033997-43.65259-128.033998-90.840903V643.229748a50.996016 50.996016 0 0 0-101.992031 0z" fill="#dbdbdb" p-id="8755"></path></svg>\n            \u5BFC\u51FA\u4F1A\u8BDD\n        </button>\n        <button id="importSession" class="btn flex justify-center gap-2 btn-dark btn-small m-auto mb-2">\n            <svg t="1670527878930" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="7606" width="16" height="16"><path d="M563.2 68.266667v573.44a51.2 51.2 0 0 1-102.4 0V68.266667a51.2 51.2 0 0 1 102.4 0z" fill="#dbdbdb" p-id="7607"></path><path d="M513.092267 616.584533l290.474666-289.518933a51.2 51.2 0 0 1 72.226134 72.4992L513.092267 761.173333 148.138667 397.448533A51.2 51.2 0 0 1 220.433067 324.949333l292.6592 291.6352z" fill="#dbdbdb" p-id="7608"></path><path d="M51.2 641.706667v185.275733c0 109.909333 105.6768 193.604267 230.946133 193.604267h459.707734c125.269333 0 230.946133-83.694933 230.946133-193.604267V641.706667a51.2 51.2 0 1 0-102.4 0v185.275733c0 47.445333-55.296 91.204267-128.546133 91.204267H282.146133c-73.250133 0-128.546133-43.8272-128.546133-91.204267V641.706667a51.2 51.2 0 0 0-102.4 0z" fill="#dbdbdb" p-id="7609"></path></svg>\n            \u5BFC\u5165\u4F1A\u8BDD\n        </button>\n        ';var j=h.querySelector('#exportSession');j.onclick=function(){var l=document.querySelector('textarea'),m=window.exportSaveData();m&&prompt('\u2193\u8BF7\u590D\u5236\u60A8\u7684\u4F1A\u8BDD\u5B58\u6863\u2193',m)};var k=h.querySelector('#importSession');for(k.onclick=function(){if(!window.location.href.includes('/chat/')&&window.location.href.includes('/chat'))return void alert('\u8BF7\u5728\u4E00\u4E2A\u60A8\u5DF2\u7ECF\u5B58\u5728\u7684\u4F1A\u8BDD\u4F7F\u7528\u8FD9\u4E2A\u529F\u80FD\uFF0C\r\n\u800C\u4E0D\u662F\u5728\u300C New Chat \u300D\u7684\u7A7A\u4F1A\u8BDD\u4E0A\u4E0B\u6587\u91CC\u9644\u52A0');var l=prompt('\u8BF7\u5728\u6B64\u7C98\u8D34\u4F1A\u8BDD\u5B58\u6863');window.importSaveData(l)},e.insertBefore(h,e.childNodes[1]),d=0;d<g.length;d++)e.childNodes[0].hasOwnProperty('patched')||(e.childNodes[0].addEventListener('click',function(l){l.preventDefault(),confirm('\u5373\u5C06\u521B\u5EFA\u65B0\u7684\u4F1A\u8BDD, \u4F7F\u7528\u5BFC\u5165\u529F\u80FD\u5BFC\u5165\u7684\u4F1A\u8BDD\u5C06\u5931\u6548,\u662F\u5426\u7EE7\u7EED?')&&(e.childNodes[0].removeEventListener('click',arguments.callee),window.clearTempValues(),e.childNodes[0].click())}),Object.defineProperty(e.childNodes[0],'patched',{value:!0,enumerable:!1}))},c=0;c<a.length;c++){var d;b()}},window.getAuthTimestamp=function(a){var b=a.split('.');if(2>b.length)return 0;var c=window.atob(b[1]),d=JSON.parse(c);return d&&d.exp?d.exp:0},window.boxInit();var oldFetch=window.fetch;window.fetch=function(){for(var a=arguments.length,b=Array(a),c=0;c<a;c++)b[c]=arguments[c];if(b[0].includes('moderations')&&window.enableFakeMod)return new Response('{}',{status:200,statusText:'ok'});if(b[0].includes('signout')&&window.enableFakeMod&&!confirm('\u662F\u5426\u8981\u9000\u51FA\u767B\u5F55\uFF1F'))return new Response('{}',{status:200,statusText:'ok'});if(b[0].includes('/conversation/')||b[0].includes('/conversations')||b[0].includes('/chat.json')){if(b[0].includes('/conversations')&&'PATCH'===b[1].method){var e=JSON.parse(b[1].body);e.is_visible=!(confirm('\u8B66\u544A:\u771F\u7684\u8981\u6E05\u7A7A\u60A8\u8D26\u6237\u4E0B\u6240\u6709\u7684\u4F1A\u8BDD\u8BB0\u5F55\uFF1F')&&confirm('\u8B66\u544A:\u7B2C\u4E8C\u6B21\u786E\u8BA4,\u6E05\u7A7A\u540E\u60A8\u5C06\u65E0\u6CD5\u627E\u56DE\u4E4B\u524D\u7684\u6240\u6709\u8BB0\u5F55!\u662F\u5426\u7EE7\u7EED\uFF1F')),e.is_visible||window.clearTempValues(),b[1].body=JSON.stringify(e)}setTimeout(window.onresize,1e3),window.clearTempValues()}else if(b[0].includes('conversation')&&b[1].body&&'POST'===b[1].method){var d=new Headers(b[1].headers),e=d.get('authorization');window.authorization_last=e;var f=window.import_authorization?window.import_authorization:e;if(d.set('authorization',f),b[1].headers=d,window.next_conversation_id&&window.next_parent_message_id){var g=JSON.parse(b[1].body);g.conversation_id=window.next_conversation_id?window.next_conversation_id:g.conversation_id,g.parent_message_id=window.next_parent_message_id?window.next_parent_message_id:g.parent_message_id,b[1].body=JSON.stringify(g),delete window.next_parent_message_id,delete window.next_conversation_id}else{var g=JSON.parse(b[1].body);window.conversation_id_last=g.conversation_id,window.parent_message_id_last=g.parent_message_id}}return oldFetch.apply(void 0,b)};var resizeTimer=null;window.onresize=function(){resizeTimer&&clearTimeout(resizeTimer),resizeTimer=setTimeout(function(){window.boxInit();for(var c,a=document.getElementsByTagName('button'),b=0;b<a.length;b++)c=a[b],-1!==c.innerHTML.indexOf('sidebar')&&c.addEventListener('click',function(){window.setTimeout(function(){window.boxInit()},300)})},200)},window.onresize(),alert('\u8D5B\u535A\u5DE5\u5177\u5A18v1.1.14\u811A\u672C\u5DF2\u542F\u7528\u3002\u672C\u5DE5\u5177\u7531ChatGPT\u5728\u6307\u5BFC\u4E0B\u751F\u6210~\r\n\r\n\u66F4\u65B0:\r\n\r\n1. \u9002\u914D\u65B0\u7248\u672C\u524D\u7AEF\u9875\u9762\r\n2. \u4FEE\u6B63\u4E86\u90E8\u5206\u811A\u672C\u7BA1\u7406\u5668\u91CD\u590D\u52A0\u8F7D\u9875\u9762\u7684\u6545\u969C(\u4E5F\u8BB8\u5427)');
```


2 . 添加一个新的书签，删除所有地址url，黏贴上去并且保存。

<img width="508" alt="image" src="https://user-images.githubusercontent.com/3683548/207085565-7b2598c1-4db1-44d3-961e-143cf089a27a.png">



3 . 在ChatGPT聊天界面点击这个书签，即可激活(远端拉取版本需要等待1~5秒)

<img width="1150" alt="image" src="https://user-images.githubusercontent.com/3683548/207087766-46563180-b562-44c6-9b5e-4b25804e30e4.png">


## 移动端 Chrome 使用指南

移动端分两种情况。

大屏设备如iPad下的Chrome可以直接添加PC版本的书签。

如果是手机等小屏设备，建议添加到书签栏之后，起一个好记的名字，自动联想之后手动点击javascript:开头的部分。



书签无法正常使用的请往下看


1 . 复制以下代码

```
var xhr=new XMLHttpRequest();xhr.open('GET','https://ghproxy.com/https://raw.githubusercontent.com/bigemon/ChatGPT-ToolBox/main/toolbox-chrome-bookmark.js',true);xhr.onload=function(){if(xhr.readyState===4&&xhr.status===200){eval(xhr.responseText)}};xhr.send(null);
```

2 . 在手机Chrome新建一个书签，黏贴并且保存

<img width="332" alt="image" src="https://user-images.githubusercontent.com/3683548/208836281-02974798-be9d-4cdc-a890-19c835cf8c21.png">


3 . 在要激活的页面，地址栏手动输入刚才的书签名并且点击

<img width="347" alt="image" src="https://user-images.githubusercontent.com/3683548/208836169-5ea30330-054c-4407-847b-7a1da5286fb4.png">



