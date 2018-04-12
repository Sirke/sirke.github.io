---
title: WebUploader上传组件
tags: WebUploader
category: WebUploader
date: 2018-03-22 20:30:36
---
![image](http://ovi3ob9p4.bkt.clouddn.com/TIETU/CT0161.jpg)

大文件上传组件
<!--more-->
#### 基本用法

`$(function(){…});   jQuery(function($) {…});  $(document).ready(function(){…})`这三个的作用是一样的，本人比较需要用第一种、书写简单。文档载入完成后执行的函数。

```js
//一个div用来存放文件上传时的信息
//一个div用来存放上传相关的按钮
<link rel="stylesheet" type="text/css" href="./web-uploader/webuploader.css" />
<!--<script style="text/javascript" src="./jQuery/jquery-2.2.3.min.js"></script>-->
<script type="text/javascript" src="./web-uploader/webuploader.js"></script>
<div id="uploader" class="wu-example">
    <!--用来存放文件信息-->
    <div id="thelist" class="uploader-list"></div>
    <div class="btns">
        <div id="picker">选择文件</div>
        <button id="ctlBtn" class="btn btn-default">开始上传</button>
        <button id="goBack" class="btn btn-default">返回</button>
    </div>
</div>
/*
1、首先用WebUploader.create创建一个 WebUploader对象 ，并在create中添加自定义配置项
2、然后手动给WebUploader对象添加事件，用到的基本事件是 
	fileQueued 文件被添加进队列的时候，在thelist div 中显示文件信息
	uploadProgress 文件上传过程中创建进度条实时显示
	uploadSuccess
	uploadError 
	uploadComplete 在文件上传完后都会触发uploadComplete事件
3、最后 调用upload()方法实现上传，
*/
<script>
var uploader = WebUploader.create({

	// swf文件路径
	swf:  '/js/Uploader.swf',
	formData:{"dn":$("#requestDn").val()},//参数列表
	// 文件接收服务端。
	server: '/tp5/index/user/uploadFile',
	// 选择文件的按钮。可选。
	// 内部根据当前运行是创建，可能是input元素，也可能是flash.
	pick: '#picker',
	// 不压缩image, 默认如果是jpeg，文件上传前会压缩一把再上传！
	resize: false,
	// 只允许选择图片文件。
	accept: {
		title: 'file',
		extensions: 'cer'
//                mimeTypes: '.cer,'
	}
});
var $list = $("#thelist");
uploader.on( 'fileQueued', function( file ) {
	$list.append( '<div id="' + file.id + '" class="item">' +
			'<h4 class="info">' + file.name + '</h4>' +
			'<p class="state">等待上传...</p>' +
			'<p class="progress progress-bar">上传进度...</p>' +
			'</div>' );
});

uploader.on( 'uploadSuccess', function( file ) {
	$( '#'+file.id ).find('p.state').text('已上传');
});
// 文件上传过程中创建进度条实时显示。
uploader.on( 'uploadProgress', function( file, percentage ) {
	var $li = $( '#'+file.id ),
			$percent = $li.find('.progress .progress-bar');

	// 避免重复创建
	if ( !$percent.length ) {
		$percent = $('<div class="progress progress-striped active">' +
				'<div class="progress-bar" role="progressbar" style="width: 0%">' +
				'</div>' +
				'</div>').appendTo( $li ).find('.progress-bar');
	}

	$li.find('p.state').text('上传中');

	$percent.css( 'width', percentage * 100 + '%' );
});
uploader.on( 'uploadError', function( file ) {
	$( '#'+file.id ).find('p.state').text('上传出错');
});

uploader.on( 'uploadComplete', function( file ) {
	$( '#'+file.id ).find('.progress').fadeOut();
});

$("#ctlBtn").on('click', function() {
	uploader.upload();
});
$("#goBack").on('click', function() {
	$("#uploadFileDiv").empty();
	$("#uploadFile").removeClass("hidden");
});
</script>
```

#### 接口说明 

这里是简单介绍，具体接口参考 

webuploader接口文档地址

Web Uploader内部类的详细说明，以下提及的功能类，都可以在 WebUploader 这个变量中访问到。

也就是说下面提到的 Base类 、Mediator类 、file类 、Queue类 都可以直接用 WebUploader 创建的变量直接访问，

例如下面创建的 uploader 变量，就可以直接访问 Base类 的 uploader.browser.ie

//Demo中使用的是WebUploader.create方法来初始化的，实际上可直接访问WebUploader.Uploader

##### Uploader类 上传入口类

###### 参数说明

下面所有参数都是可选的，并且都有默认值

```js
	var uploader = WebUploader.Uploader({	
		//几个常用的参数：swf,pick,formData,runtimeOrder
		
		//所有参数列表
		swf: 'path_of_swf/Uploader.swf',
		dnd: '#dndArea', // [默认值：undefined] 指定Drag And Drop拖拽的容器，如果不指定，则不启动。
		disableGlobalDnd: true,, // [默认值：false] 是否禁掉整个页面的拖拽功能，如果不禁用，图片拖进来的时候会默认被浏览器打开
		paste: '#uploader', // [默认值：undefined] 指定监听paste事件的容器，如果不指定，不启用此功能。此功能为通过粘贴来添加截屏的图片。建议设置为document.body.
		pick:'#filePicker',//也可以用下面的方式详细配置
		// {Selector, Object}  [默认值：undefined] 指定选择文件的按钮容器，不指定则不创建按钮。
		pick: {
			id: '#filePicker',//Seletor|dom 指定选择文件的按钮容器，不指定则不创建按钮。注意 这里虽然写的是 id, 但是不是只支持 id, 还支持 class, 或者 dom 节点。
			label: '点击选择图片',//请采用 innerHTML 代替
			innerHTML: "点击选择图片",// 指定按钮文字。不指定时优先从指定的容器中看是否自带文字。
			multiple:true //是否开起同时选择多个文件能力。
		},
		//限制上传的文件类型
		accept: {
			title: 'Images',// {String} 文字描述
			extensions: 'gif,jpg,jpeg,bmp,png,rar',// {String} 允许的文件后缀，不带点，多个用逗号分割。
			mimeTypes: 'image/gif，image/jpg，image/jpeg，image/bmp，image/png，.rar'// 多个用逗号分割。
		},
		// 设置缩略图。
		thumb: {
			width: 110,
			height: 110,
			// 图片质量，只有type为`image/jpeg`的时候才有效。
			quality: 70,
			// 是否允许放大，如果想要生成小图的时候不失真，此选项应该设置为false.
			allowMagnify: true,
			// 是否允许裁剪。是否采用裁剪模式。如果采用这样可以避免空白内容。
			crop: true,
			// 为空的话则保留原有图片格式。
			// 否则强制转换成指定的类型。
			type: 'image/jpeg'
		},
		// 配置压缩的图片的选项。如果此选项为false, 则图片在上传前不进行压缩。
		compress: {
			width: 1600,
			height: 1600,
			// 图片质量，只有type为`image/jpeg`的时候才有效。
			quality: 90,
			// 是否允许放大，如果想要生成小图的时候不失真，此选项应该设置为false.
			allowMagnify: false,
			// 是否允许裁剪。
			crop: false,
			// 是否保留头部meta信息。
			preserveHeaders: true,
			// 如果发现压缩后文件大小比原来还大，则使用原来图片
			// 此属性可能会影响图片自动纠正功能
			noCompressIfLarger: false,
			// 单位字节，如果图片大小小于此值，不会采用压缩。
			compressSize: 0
		}, 


		auto: true, // [默认值：false] 设置为 true 后，不需要手动调用上传，有文件选择即开始上传。
		runtimeOrder: 'flash', // [默认值：html5,flash] 指定运行时启动顺序。默认会想尝试 html5 是否支持，如果支持则使用 html5, 否则则使用 flash.可以将此值设置成 flash，来强制使用 flash 运行时。
		prepareNextFile:false, // [默认值：false] 是否允许在文件传输时提前把下一个文件准备好。 对于一个文件的准备工作比较耗时，比如图片压缩，md5序列化。 如果能提前在当前文件传输期处理，可以节省总体耗时。
		chunked:false, // [默认值：false] 是否要分片处理大文件上传。
		chunkSize: 512 * 1024,// [默认值：5242880] 如果要分片，分多大一片？ 默认大小为5M.
		chunkRetry:2, // [默认值：2] 如果某个分片由于网络问题出错，允许自动重传多少次？
		threads:3, // [默认值：3] 上传并发数。允许同时最大上传进程数。
		formData: {"data":"value","data":"value"}, // [默认值：{}] 文件上传请求的参数表，每次发送都会发送此对象中的参数。
		fileVal:"file", // [默认值：'file'] 设置文件上传域的name。
		method :"POST", // [默认值：'POST'] 文件上传方式，POST或者GET。
		sendAsBinary :false, // [默认值：false] 是否已二进制的流的方式发送文件，这样整个上传内容php://input都为文件内容， 其他参数在$_GET数组中。
		fileNumLimit :10, // [默认值：undefined] 验证文件总数量, 超出则不允许加入队列。
		fileSizeLimit : 200 * 1024 * 1024,    // 200 M  [默认值：undefined] 验证文件总大小是否超出限制, 超出则不允许加入队列。
		fileSingleSizeLimit: 50 * 1024 * 1024,    // 50 M [默认值：undefined] 验证单个文件大小是否超出限制, 超出则不允许加入队列。
		duplicate :true, // [默认值：undefined] 去重， 根据文件名字、文件大小和最后修改时间来生成hash Key.
		disableWidgets: {String, Array}, // [默认值：undefined] 默认所有 Uploader.register 了的 widget 都会被加载，如果禁用某一部分，请通过此 option 指定黑名单。
	});
```

###### uploader对象的选项

```js
	1、option() //获取或者设置Uploader配置项。
	// 修改后图片上传前，尝试将图片压缩到1600 * 1600
	uploader.option( 'compress', {
		width: 1600,
		height: 1600
	});	
	2、getStats() //获取文件统计信息。返回一个包含一下信息的对象。
	//successNum 上传成功的文件数
	//progressNum 上传中的文件数
	//cancelNum 被删除的文件数
	//invalidNum 无效的文件数
	//uploadFailNum 上传失败的文件数
	//queueNum 还在队列中的文件数
	//interruptNum 被暂停的文件数
	stats = uploader.getStats();
	if ( stats.successNum && !stats.uploadFailNum ) {
		setState( 'finish' );
		return;
	}
	3、destroy() //销毁 webuploader 实例
	4、addButton() //添加文件选择按钮，如果一个按钮不够，需要调用此方法来添加。参数跟options.pick一致。
		uploader.addButton({
			id: '#filePicker2',
			label: '继续添加'
		});
	5、makeThumb() //生成缩略图，此过程为异步，所以需要传入callback。 通常情况在图片加入队里后调用此方法来生成预览图以增强交互效果。
				//当 width 或者 height 的值介于 0 - 1 时，被当成百分比使用。
				//callback中可以接收到两个参数。
				//第一个为error，如果生成缩略图有错误，此error将为真。
				//第二个为ret, 缩略图的Data URL值。
				//注意 Date URL在IE6/7中不支持，所以不用调用此方法了，直接显示一张暂不支持预览图片好了。 也可以借助服务端，将 base64 数据传给服务端，生成一个临时文件供预览。
		uploader.makeThumb( file, function( error, src ) {
		var img;

		if ( error ) {
			$wrap.text( '不能预览' );
			return;
		}

		if( isSupportBase64 ) {
			img = $('<img src="'+src+'">');
			$wrap.empty().append( img );
		} else {
			$.ajax('../../server/preview.php', {
				method: 'POST',
				data: src,
				dataType:'json'
			}).done(function( response ) {
				if (response.result) {
					img = $('<img src="'+response.result+'">');
					$wrap.empty().append( img );
				} else {
					$wrap.text("预览出错");
				}
			});
		}
	}, thumbnailWidth, thumbnailHeight );
	
	6、md5File()// 计算文件 md5 值，返回一个 promise 对象，可以监听 progress 进度。
	7、addFiles()  //添加文件到队列
	8、removeFile()  //移除某一文件, 默认只会标记文件状态为已取消，如果第二个参数为 true 则会从 queue 中移除
	9、getFiles()  //返回指定状态的文件集合，不传参数将返回所有状态的文件。
	10、retry() //重试上传，重试指定文件，或者从出错的文件开始重新上传。
	11、sort() //排序队列中的文件，在上传之前调整可以控制上传顺序。
	12、reset() //重置uploader。目前只重置了队列。
	13、predictRuntimeType() //预测Uploader将采用哪个Runtime
	14、upload() //开始上传。此方法可以从初始状态调用开始上传流程，也可以从暂停状态调用，继续上传流程。可以指定开始某一个文件
	15、stop() //暂停上传。第一个参数为是否中断上传当前正在上传的文件。如果第一个参数是文件，则只暂停指定文件。
	16、cancelFile() //标记文件状态为已取消, 同时将中断文件传输。
	17、isInProgress() //判断Uplaoder是否正在上传中。
	18、skipFile() //掉过一个文件上传，直接标记指定文件为已上传状态。
	19、request() //发送命令。当传入callback或者handler中返回promise时。返回一个当所有handler中的promise都完成后完成的新promise。
	
	20、Uploader.register() //添加组件
	21、Uploader.unRegister() //删除插件，只有在注册时指定了名字的才能被删除。
```

###### 事件说明

```js
dndAccept :// 阻止,此事件可以拒绝某些类型的文件拖入进来。目前只有 chrome 提供这样的 API，且只能通过 mime-type 验证。
beforeFileQueued :// 当文件被加入队列之前触发，此事件的handler返回值为false，则此文件不会被添加进入队列。
fileQueued :// 当文件被加入队列以后触发。
filesQueued :// 当一批文件添加进队列以后触发。
fileDequeued :// 当文件被移除队列后触发。
reset :// 当 uploader 被重置的时候触发。
startUpload :// 当开始上传流程时触发。
stopUpload :// 当开始上传流程暂停时触发。
uploadFinished :// 当所有文件上传结束时触发。
uploadStart :// 某个文件开始上传前触发，一个文件只会触发一次。
uploadBeforeSend :// 当某个文件的分块在发送前触发，主要用来询问是否要添加附带参数，大文件在开起分片上传的前提下此事件可能会触发多次。
uploadAccept :// 当某个文件上传到服务端响应后，会派送此事件来询问服务端响应是否有效。如果此事件handler返回值为false, 则此文件将派送server类型的uploadError事件。
uploadProgress :// 上传过程中触发，携带上传进度。
uploadError :// 当文件上传出错时触发。
uploadSuccess :// 当文件上传成功时触发。
uploadComplete :// 不管成功或者失败，文件上传完成时触发。
error :// 当validate不通过时，会以派送错误事件的形式通知调用者。通过upload.on('error', handler)可以捕获到此类错误，目前有以下错误会在特定的情况下派送错来。
		//Q_EXCEED_NUM_LIMIT 在设置了fileNumLimit且尝试给uploader添加的文件数量超出这个值时派送。
		//Q_EXCEED_SIZE_LIMIT 在设置了Q_EXCEED_SIZE_LIMIT且尝试给uploader添加的文件总大小超出这个值时派送。
		//Q_TYPE_DENIED 当文件类型不满足时触发。。
/*Web Uploader内部类的详细说明，以下提及的功能类，都可以在`WebUploader`这个变量中访问到。 即 Base类 Mediator类  File类都可以在`WebUploader`这个变量中访问到*/ 
```

##### Base类 

基础类方法 WebUploader 基础类，提供一些简单常用的方法  WebUploader.browser.ie

```js
	create() //创建Uploader实例，等同于new Uploader( opts );
	version //当前版本号
	$//引用依赖的jQuery或者Zepto对象
	browser  //简单的浏览器检查结果
	os  android、ios
	inherits //实现类与类之间的继承
	noop  //一个不做任何事情的方法。可以用来赋值给默认的callback
	bindFn //返回一个新的方法，此方法将已指定的context来执行
	log //引用Console.log如果存在的话，否则引用一个空函数noop。
	slice //被uncurrythis的数组slice方法。 将用来将非数组对象转化成数组对象
	guid //生成唯一的ID
	formatSize //格式化文件大小, 输出成带单位的字符串
	Deferred //创建一个Deferred对象。 详细的Deferred用法说明，请参照jQuery的API文档。Deferred对象在钩子回掉函数中经常要用到，用来处理需要等待的异步操作。
	isPromise //判断传入的参数是否为一个 promise 对象。
	when //返回一个promise，此promise在所有传入的promise都完成了后完成
```

##### Mediator类 

事件处理类，可以独立使用，也可以扩展给对象使用 中介，它本身是个单例，但可以通过installTo方法，使任何对象具备事件行为。 主要目的是负责模块与模块之间的合作，降低耦合度

```js
on once off trigger installTo 
```

##### File类 

文件类  本类的一般在 UploadProgress 这些事件中的回调函数中变量使用比较多

```js
	name//文件名，包括扩展名（后缀）
	size//文件体积（字节）
	type//文件MIMETYPE类型，与文件类型的对应关系请参考http://t.cn/z8ZnFny
	lastModifiedDate//文件最后修改日期
	id//文件ID，每个对象具有唯一ID，与文件名无关
	ext//文件扩展名，通过文件名获取，例如test.png的扩展名为png
	statusText//状态文字说明。在不同的status语境下有不同的用途。
	setStatus//设置状态，状态变化时会触发change事件。
	setStatus( status[, statusText] );//参数:status {File.Status, String}文件状态值
	statusText //{String} [可选] [默认值: ''] 状态说明，常在error时使用，用http, abort,server等来标记是由于什么原因导致文件错误。
	File.Status//文件状态值，具体包括以下几种类型：
	inited //初始状态
	queued //已经进入队列, 等待上传
	progress //上传中
	complete //上传完成。
	error //上传出错，可重试
	interrupt //上传中断，可续传。
	invalid //文件不合格，不能重试上传。会自动从队列中移除。
	cancelled //文件被移除。
```

##### Queue 类 

文件队列, 用来存储各个状态中的文件

```js
	stats//统计文件数。
	numOfQueue //队列中的文件数。
	numOfSuccess //上传成功的文件数
	numOfCancel //被取消的文件数
	numOfProgress //正在上传中的文件数
	numOfUploadFailed //上传错误的文件数。
	numOfInvalid //无效的文件数。
	numofDeleted //被移除的文件数。
	append//将新文件加入对队列尾部
    prepend//将新文件加入对队列头部
    getFile//获取文件对象
    fetch//从队列中取出一个指定状态的文件。
    sort//对队列进行排序，能够控制文件上传顺序。
    getFiles//获取指定类型的文件列表, 列表中每一个成员为File对象。
    removeFile//在队列中删除文件。
```

​	github中的代码给的例子基本上可以实现想要的功能，如果有别的需求可以结合代码中的例子根据接口手册进行相应的修改。


​	Web Uploader的所有代码都在一个内部闭包中，对外暴露了唯一的一个变量WebUploader，所以完全不用担心此框架会与其他框架冲突。
Uploader实例具有Backbone同样的事件API：`on，off，once，trigger。`
如同Document Element中的onEvent一样，他的执行比on添加的handler的要晚。如果那些handler里面，有一个return false了，此onEvent里面是不会执行到的

```js
uploader.on( 'fileQueued', function( file ) {
    // do some things.
});
//或
uploader.onFileQueued = function( file ) {
    // do some things.
};
```
