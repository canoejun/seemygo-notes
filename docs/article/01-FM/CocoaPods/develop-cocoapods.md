# 开发框架的人需要做

## 上传项目到 GitHub, 并且打好标签

```bash
git push origin master
git tag '1.0.0' 
git push --tags 
```

## 注册 trunk

```bash
pod trunk register wangshunzi@520it.com 'wangshunzi'  --verbose
```

* `--verbose` 参数是为了便于输出注册过程中的调试信息
* 成功图解
	
![](image/3_图解1.png)
		
---
		
![](image/3_图解2.png)

## 配置并上传框架的 PodSpec 文件

### 理论

* PodSpec 文件 描述自己的框架信息
	* 作者，版本，下载地址等等
* `pod search` 搜索框架, 就是根据这里面的信息进行检索的
* 注意: 一般这个文件的名称和工程名称保持一致
* 创建命令
	
	```bash
	pod spec create 文件名称
	```

### 文件内容格式

* 可以下载被cocoapods管理的框架里面的描述信息，也可以到官网查看
* 手动验证
	
	```bash	
	pod spec lint podspec文件	
	```

### 通过 trunk 推送 podspec 文件

```bash
pod trunk push 
```
	
* 注意: 
	* 这种方式其实就是上传这个描述文件到 CocoaPods 在 GitHub 上的仓库中
		[https://github.com/CocoaPods/Specs](https://github.com/CocoaPods/Specs)
	* 你也可以按照正常的操作，先 fork ，然后提交 pull request

### 等待审核

* 跟 `pull request` 一样，需要作者同意，不过现在较快

![](image/3_等待审核.png)

## 更新本地pod 第三方框架信息数据源

```bash
pod setup
```

## 测试

* 使用 `pod search` 命令搜索自己的框架, 如果可以搜索到, 那么代表审核通过了

![](image/3_审核通过.png)
		