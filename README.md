### 完整示例可导入示例项目运行
不要期待更新，我很懒~

希望能帮到你！

---

## 使用说明
| 属性| 是否必填|  值类型| 返回值| 说明|
| --------- | -------- | -----: | --: | --: |
| @up-success|否 | CallBack|{name,data} | 上传成功回调|

## ref调用
|作用 | 方法| 传入参数类型|  说明|
|---- | --------- | -------- | --: |
|下载| download|<URL,type>| type='local'为保存到本地，默认为获取临时路径|
|预览| open|URL| 预览文件|
|上传| upload|Object| 上传文件|

### vue:
``` javascript
<l-file 
	ref="lFile" 
	@up-success="upSuccess"
></l-file>
```

### js：
``` javascript
import lFile from '@/components/l-file/l-file.vue'
components:{lFile}
```
---
* 函数说明


``` javascript
/* 预览临时文件 */
this.$refs.lFile.download(url)
.then(path=>{
	this.$refs.lFile.open(path);
});

/* 保存到本地 */
this.$refs.lFile.download(url,'local')
.then(path=>{
	this.localPath = path;
});

/* 
选择文件并上传

currentWebview=当前窗口，仅app端需要传，且必传

url=上传服务器地址，必填
name=上传文件的key(选填，默认为file)
header=请求头(选填)
*/
this.$refs.lFile.upload({
	// #ifdef APP-PLUS
	currentWebview: this.$mp.page.$getAppWebview(),
	// #endif
	url: 'https://www.example.com/upload', //测试地址，记得更换
	name: 'file',
	//header: {'Content-Type':'类型','Authorization':'token'},
	//...其他参数
});


```