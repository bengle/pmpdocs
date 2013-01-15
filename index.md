<link type="text/css" rel="stylesheet" href="./bootstrap.min.css" />
# PMP项目前端文档

***

#### [app-audit(卖家后台弹出层iframe页面)](#app-audit)
#### [add-special(添加专场)](#add-special)
#### [album-list（专场列表）](#album-list)
#### [auction-list（拍品列表主要用于专场详情和卖家档案里面的iframe）](#auction-list)
#### [p-list（拍品搜索列表主搜页面）](#p-list)
#### [option-list（卖家后台操作页面）](#option-list)
#### [more-auction（精品拍卖——拍卖集市首页）](#more-auction)
#### [shop-located（商家入驻）](#shop-located)
#### [special-detail（专场详情）](#special-detail)
#### [common（公共文件）](#common)
#### [utils（组件文件）](#utils)

***

PMP项目采用kissy-pie工具打包，使用方法请参考：https://github.com/maxbbn/front-build

***

#### 1. <span id="app-audit">app-audit</span>
> 文件描述：卖家后台（专场发布和卖家后台管理）弹出层iframe页面，主要包括：添加拍品、加入专场等操作。包括文件list.css,listAction.js。

  * listAction.js：
  
    构造函数：ListAction
    
    	- 包含方法init（）初始化所有功能模块主要包括instance（）和bindEvents（）两个方法。调用方法：ListAction.init();
    
    functions：
    
    	1. instance（）页面加载后初始化页面数据和动画效果。
    	2. bindEvents（）绑定页面所有事件。
    	3. feedbackAnim（）
       		param：
       			- actionJoinStat； type：boolean，表示操作成功失败。
       		功能：根据actionJoinStat动画显示成功/错误提示信息。  
    	4. animRun（）
       		param：
       			- selector；type：String，提示框元素选择符；
       			- auctionJoinStat；type：boolean，表示操作成功失败。
       		功能：动画显示成功/错误提示框。


#### 2. <span id="add-special">add-special</span>
> 文件描述：卖家后台添加专场页面，用于卖家添加拍卖专场。包括字段：经营类目、专场标签、专场标题、专场图片、专场描述、专场资讯、拍品数、拍品报名与添加拍品。包括文件：audit.css,auditAction.js,auditControl.js,cateControl.js,cateViews.js,category.css,commodityAction.js,editor.js,formControl.js,frame.css,infoControl.js,infoViews.js,information.css,popup.css,refuse.js,uploader.js

  * cateControl.js
  
  	> 对应经营类目以及子类目
  
  	构造函数：CateControl
  		- 调用init（）方法初始化所有功能，包括bindEvents（）方法。
  	
  	functions：
  		1. bindEvents（）
  			功能：绑定类目模块的所有事件。
  		2. updateDefaultList（）
  			功能：根据类目checkbox的change事件显示或隐藏对应的子类目。
  * cateViews.js（已失效）
  * infoControl.js
  
  	> 对应专场标签、专场标题、专场图片、专场描述、专场资讯、拍品数
  	
  	构造函数：Information
  		- 调用init（）初始化该部分所有功能，包括图片上传组件、副文本编辑器组件、字符串截取省略组件和bindEvents（）方法。
  	
  	functions：
  		1. initTextLimit（）
  			功能：设置专场标签、专场标题、专场描述的最大填写长度。
  		2. bindEvents（）
  			功能：绑定该部分所有事件。
  * infoViews.js（已失效）
  * uploader.js
  
  	> 专场图片上传
  	
  	构造函数：ImageUploader
  		- 调用init（）方法初始化上传组件。
  	
  	functions：
  		1. uploaderInit（）	
  			功能：初始化上传组件。
  		2. hideErrorTip（）	
  			功能：隐藏专场图片的错误提示。
  * editor.js
  
  	> 专场资讯的编辑器
  	
  	模块全局参数：
  		
  		- editorCount：专场资讯的数量，默认是1；
  		- cfg：编辑器的配置参数；
  		- pluginConfig：编辑器插件的配置参数；
  	
  	构造函数：EditorModule
  		- 调用init（）方法初始化编辑器所有功能，包括instance（）、editorInit（）和bindEvents（）。
  	
  	functions：
  	
  		1. instance（）
  			功能：页面加载后初始化编辑器的数量和配置
  		2. editorInit（）
  			功能：初始化默认的第一个编辑器。
  		3. bindEvents（）
  			功能：绑定专场资讯模块的所有事件。
  * auditControl.js
  
  	> “添加拍品”模块功能
  	
  	模块全局参数：
  	
  		- addSuggestUrl，设置推荐拍品的请求url；
  		- removeSuggestUrl，取消设置推荐拍品的请求url；
  		- suggestCount，推荐拍品的数量；
  	
  	构造函数：AuditControl
  		- 调用init（）方法初始化添加拍品所有功能（dialogAction、refuseModule），包括instance（）、bindEvnets（）。
  		
  	functions：
  	
  		1. instance（）
  			功能：页面加载完成后初始化添加拍品的数据和参数；
  		2. bindEvents（）
  			功能：绑定添加拍品区域所有事件。
  * auditAction.js
  
  	> “添加拍品”区域中设置拍品推荐和取消推荐功能。
  	
  	构造函数：AuditAction
  		- 包括方法addSuggestion（）和removeSuggestion（）。
  	
  	functions：
  	
  		1. addSuggestion（）
  			param：
  				- addSuggestionUrl，设置拍品推荐的异步请求url；
  				- parentNode，对应拍品的节点；
  			功能：设置拍品为推荐。
  		2. removeSuggestion（）
  			param：
  				- removeSuggestionUrl，取消拍品推荐的异步请求url；
  				- parentNode，对应拍品的节点；
  			功能：取消拍品推荐设置。
  * commodityAction.js
  
  	> 拍品操作功能模块。
  	
  	构造函数：CommodityAction
  		- 包含方法deletCommodity（）。
  		
  	functions：
  		
  		1. deletCommodity（）
  			param：
  				- listNode，对应拍品节点；
  			功能：删除拍品后去掉拍品节点的动画效果。
  * formControl.js
  
  	> 专场发布和专场编辑表单验证功能。
  	
  	构造函数：FormControl
  		- 调用init（）初始化表单验证功能模块（Auth组件），包括initFormValidate（）。
  		
  	functions：
  		
  		1. initFormValidate（）
  			功能：初始化Auth组件
  * refuse.js
  
  	> 审核拍品操作中拒绝操作弹出层及功能。
  	
  	模块全局参数：
  	
  		- albumId，专场id；
  		- action，拒绝拍品请求的action参数；
  		- event_submit_do_ot_pass，拒绝拍品请求的event_submit_do_ot_pass参数；
  		- _tb_token_，拒绝拍品请求的_tb_token_参数；
  		- productId，拒绝拍品请求的auctionId参数；
  		- target，拒绝拍品的点击对象；
  		- refuseUrl，拒绝拍品的异步请求url；
  		
  	构造函数：RefuseModule
  	
  		- 调用init（）初始化拒绝拍品加入专场功能，包括instance（）、bindEvents（）和createRefuseDialog（）。
  		
  	functions：
  	
  		1.	instance（）
  			功能：初始化拒绝模块参数。
  		2.	bindEvents（）
  			功能：绑定拒绝弹出层的所有事件。
  		3.	createRefuseDialog（）
  			param：
  				- itemId，拍品id；
  				- self，点击的对象；
  			功能：创建拒绝的弹出层。
  		4.	buildRefuseDialog()
  			功能：生成弹出层内部的html。
  		5.	makeRefuseDialog（）
  			param：
  				- dialogContent，弹出层内的html；
  			功能：生成弹出层。
  		6.	submitRefuse()
  			param:
  				- itemId，拍品id；
  				- reason，拒绝理由；
  				- self，点击对应元素；
  			功能：异步提交拒绝添加拍品到专场。

#### 3. <span id="album-list">album-list</span>
> 文件描述：专场列表和卖家档案页面，根据日期显示对应日期发布的专场以及卖家信息和所属拍品。包括文件：album-banner.css，album-list.css，album-list.js，dateModule.js，seller-banner.css

  * album-list.js
  
  	构造函数：AlbumList
  	
  		- 包含方法init（）初始化所有功能模块包括instance（）、msg组件初始化和initSellerData（）方法。调用方法：AlbumList.init();
  	
  	functions:
  	
  		1. instance() 页面初始化后初始化msg组件和textlimited组件
  		2. initSellerData()
  			param：
  				- sellerDataUrlId；type：string，卖家拍品信息的ajax请求地址所在元素的选择器。
  				- sellerAuctionNumId；type：string，显示卖家拍品数量的容器选择器。
  			功能：卖家档案页面加载完成后异步请求卖家拍品数量并更新到页面。
  	
  * dateModule.js
  	
  	模块描述：专场列表页面中日期模块js脚本。
  	
  	模块全局参数：
  	
  			- weekArray 日历中日期坐标。
  			- updateDateUrl 获取上一周/下一周日期的异步接口url。
  	
  	构造函数：DateModule
  	
  		- 包含方法init（）初始化所有功能模块包括instance（）和bindEvents（）。调用方法：DateModule.init()；
  	
  	functions：
  	
  		1. instance() 初始化页面数据。
  		2. bindEvents（）绑定页面所有事件。
  		3. initCursorPos（）初始化当前日期的箭头坐标。
  		4. updateDateContent（）
  			param：
  				- newWeek；type：Obj，新一周的日期对象
  			功能：点击“前一周”“后一周”按钮后更新当前周的日期。
  		5. updateParamDate（）
  			param：	
  				- newDate；type：string，当前周周一的日期
  			功能：更新“前一周”“后一周”按钮上的param-date伪属性


#### 4. <span id="auction-list">auction-list</span>
> 文件描述：搜索拍品列表，由于拍品搜索后台分为数据库搜索与主搜搜索，本目录文件用于主搜情况下专场列表页和卖家档案页面的拍品列表iframe，主要包括列表模式和大图模式。包括文件：option-bar.css,options.css,p-list.css,p-list.js。

* p-list.js
	
	构造函数：ListFunc
	
		- 包含方法init（）初始化所有功能模块，包括instance（）和bindEvents（）方法。调用方法：ListFunc.init()；
	
	functions：
	
		1. instance（）初始化页面数据。
		2. bindEvents（）绑定页面所有事件。
		3. getAllItemId（）
			功能：获取页面所有拍品的id拼成字符串。	
			returns：allId，type：string，所有拍品id用“，”链接后的字符串。
		3. mppCallback（）
			功能：长连接的callback函数，延时拍时更新拍品的结束时间和所有拍品的当前价、出家次数等信息。
		4. removeMoreMargin（）
			功能：该功能已经取消。
		5. removeOptBarBorder（）
			功能：取消拍品列表iframe的top-border。
		6. fixIframeSize（）
			功能：拍品列表iframe宽高自适应。


#### 5. <span id="p-list">p-list</span>
> 文件描述：搜索拍品列表，搜索栏搜索结果页面，包括列表模式和大图模式。包括文件：category-bar.css,detail.css,option-bar.css,options.css,p-list.css,p-list.js。

* p-list.js

	构造函数：ListFunc
	
		- 包含方法init（）初始化所有功能模块，包括instance（）和bindEvents（）方法。调用方法：ListFunc().init()；
	
	functions：
	
		1. instance（）
			功能：初始化页面数据。初始化textlimited和scroller组件。
		2. bindEvents（）
			功能：绑定页面所有事件。
		3. removeMoreMargin（）
			功能：取消类目列表中“其他类目”容器的margin-top。


#### 6. <span id="option-list">option-list</span>
> 文件描述：卖家后台管理页面，主要包括：拍品操作、专场操作和可报名专场3个页面。包括文件：listAction.js,lists.css,struts.css。

* listAction.js

	模块全局参数：
	
		- sessionUrl：报名专场的异步请求url
		- commodityUrl：添加拍品的异步请求url
		- figureUrl：页面初始化获取卖家信息数据的url


	构造函数：ListAction
	
		- 包含方法init（）初始化所有功能模块。包括instance（）和bindEvents（）。调用方法：ListAction.init()；
	
	functions：
	
		1. instance（）
			功能：初始化页面数据。初始化textlimited和dialogaction组件。
		2. bindEvents（）
			功能：绑定页面所有事件。
		3. getFigureUrl（）
			功能：从隐藏域中得到请求卖家信息数据的url。
		4. updateFigures（）
			功能：异步请求卖家信息的数据，更新到“我的拍品”、“我的专场”和“可报名专场”。
		5. fixSidebarHeight()
			功能：左边栏高度自适应。
		6. feedbackAnim（）
			param：auctionJoinStat，type：string|‘T’or‘F’，操作成功失败的状态。
			功能：“添加拍品”，“报名专场”等操作后的结果提示框动画。
		7. animRun（）
			param：
				- selector：type：string，提示弹出框的选择器。
				- auctionJoinStat：type：string|‘T’or‘F’，操作成功失败的状态。
			功能：动画显示操作结果提示框。
		8. applySession()
			param：	
				- sessionUrl：type：string，加入专场的异步请求url。
				- self：type：obj，按钮的对象。
			功能：异步请求加入专场。
		9. applyCommodity（）
			param：
				- commodityUrl：type：string，添加拍品的异步请求url。
				- self：type：obj，按钮对象。
			功能：异步请求添加拍品。


#### 7. <span id="more-auction">more-auction</span>
> 文件描述：精品拍卖页面，也就是拍卖集市首页，本页面是TMS页面，地址是：http://www.taobao.com/go/chn/auctionmarket.php。包括文件：banner.css，banner.js，brand.css，brand.js，category.css，category.js，market.css，market.js

* category.js

	构造函数：Category
	
		- 调用init（）方法初始化所有功能。包括instance（）方法。
	functions：
	
		1. instance()，页面加载完成后初始化类目栏功能和数据。
		2. initCatesBtn（）给每一个类目按钮设置定位。



#### 8. <span id="shop-located">shop-located</span>
> 文件描述：商家入驻流程页面，商家入驻是商家参与PMP拍卖的必要条件，主要包括：入驻条款、保证金和服务费、入驻结果3个页面。包括文件：located.css，settle.js，sprites.css。

* settle.js

	模块全局参数：
	
		1. guaranty：保证金额度，初始值是0；
		2. service：服务费额度，初始值是0；


	构造函数：SettleModule
	
		- 包括方法init（）初始化所有功能。包括instance（）和bindEvents（）方法。
	
	functions：
	
		1. instance（），页面加载完成后初始化页面的模块和数据。
		2. bindEvents（），绑定页面所有事件。
		3. initCateInput（）， 提交或修改保证金与服务费页面加载完成后，根据所有checkbox的伪属性data-modify更改对应的选中状态。
		4. updatePrice（），
			param：	
				- guaranty：保证金额度，初始值是0；
				- service：服务费额度，初始值是0；
			功能：根据卖家选的类目更新其所付保证金和服务费的数值。
		5. addCommas（）
			param：		
				- num：选中的类目对应金额；
			功能：每选中或者取消一项类目重新计算保证金和服务费。


#### 9. <span id="special-detail">special-detail</span>
> 文件描述：专场详情页面，主要包括专场描述和所有拍品两部分。所有拍品有两种显示方式：数据库搜索，结果直接显示在页面上；主搜搜索，结果显示在iframe中，详情见 <a href="#auction-list">auction-list</a>。包括文件：album-detail.js，category-bar.css，detail.css，option-bar.css，options.css，p-list.css。

* album-detail.js

	模块全局参数：
	
		1. timer：计时器组件；
		2. msg：长连接组件；
	构造函数：
	
		AlbumDetail，包括init（）初始化所有功能和textlimited组件。包括instance（）。
		
	functions：
	
		1. instance（）	
			功能：页面加载完成后初始化功能函数（计时器组件、长连接组件）和数据。
		2. updateLeftTime()	
			功能：该功能已经废弃。



#### 10. <span id="common">common</span>
> 文件描述：所有页面公用文件，主要是统一页头页尾以及js脚本加载配置文件。

#### 11. <span id="utils">utils</span>
> 文件描述：多页面用的组件文件，使用kissy包机制引入，打包后会一起打包进入对应页面目录中，如有更改可使用kissy-pie的build all命令将所有页面文件夹重新打包。

