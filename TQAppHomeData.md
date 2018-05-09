## DTO 数据模型

* TQHomeDataInfo

```
NSArray *homeDataList;  /*!< 首页列表配置数据 TQHomeStyleInfo array */
NSArray *carItemList;	//猜你喜欢  车辆信息DTO 数组
```


* TQHomeStyleInfo 

```
NSNumber *style;        /*!< 样式 */
NSNumber *rank;        	 /*!< 排序 */
NSString *info;         /*!< 样式说明，可选 */
NSString *moduleImgUrl; /*!< 模块用到的图片URL,平台介绍模块用到 */ 
NSArray *contentList;   /*!< 数组样式用 TQHomeActionInfo array */
NSArray *contentScrollList;   	/*!< 横向滚动列表 二维数组 */
TQHomeActionInfo *contentInfo;   /*!< 单数据样式用 TQHomeActionInfo */
```

* TQHomeActionInfo

```
NSString *title;            /*!< 标题 */
NSString *subTitle;         /*!< 副标题 */
NSString *iconUrl;          /*!< 图片url */
NSString *picUrl;           /*!< 背景url */
NSString *tagUrl;           /*!< 标签图url */
NSString *actionUrl;        /*!< 动作URI */
NSString *color;            /*!< 颜色 （首页线索登记模块）用到 */
NSNumber *width;            /*!< 图片宽 */
NSNumber *height;           /*!< 图片高 */
BOOL marketing;           	 /*!< 是否有营销活动 倒计时 */
TQMarketInfo *marketInfo;   /*!< 市场营销数据  marketing 为 true 时 使用 */
```

* TQMarketInfo

```
NSString *startTime;        /*!< 开始时间戳 */
NSString *endTime;          /*!< 结束时间戳 */
NSString *beforeImgUrl;     /*!< 活动前图片 */
NSString *beforeActionUrl;  /*!< 活动前点击事件URL */
NSString *ingImgUrl;        /*!< 活动中图片 */
NSString *ingActionUrl;     /*!< 活动中点击事件URL */
NSString *afterImgUrl;      /*!< 活动后图片 */
NSString *afterActionUrl;   /*!< 活动后点击事件URL */
```

## 样式数据说明

* 下发数据 JSON 对象

```
{
	"carItemList" : [],		//猜你喜欢 车辆信息DTO数组
	"homeDataList" : [
		//TQHomeStyleInfo 模型的 DTO 数组
		{
			"style" : "样式ID",        /*!< 样式 */
			"info": "样式说明", 
			"moduleImgUrl": "模块用到的图片URL", /*!< 平台介绍模块用到 */ 
 			"rank": 0,  	 				/*!< 排序 */
			//内部为列表数据时使用 contentList
			//内部为单一元素时使用 contentInfo
			//多行横向滚动列表使用 contentScrollList   
			//contentList、contentInfo、contentScrollList 不会同时使用
			"contentList" : [], //TQHomeActionInfo DTO 数组
			"contentScrollList" : [	 //二维数组  多行横向滚动列表
				[],	//TQHomeActionInfo DTO 数组
				[]	//TQHomeActionInfo DTO 数组
			],
			"contentInfo" : 	//TQHomeActionInfo DTO
				{
					"title" : "",            /*!< 标题 */
					"subTitle": "",         /*!< 副标题 */
					"picUrl": "",           /*!< 背景url */
					"iconUrl": "",          /*!< 图片url */
					"tagUrl": "",           /*!< 标签图url */
					"actionUrl": "",       	/*!< 动作URI */
					"color": "",            /*!< 颜色 （首页线索登记模块）用到 */
					"width": "",            /*!< 图片宽 动态设置模块大小时用到 */
					"height": "",           /*!< 图片高 动态设置模块大小时用到 */
					"marketing": false,     /*!< 是否有营销活动 倒计时 */
					"marketInfo": 			/*!< 市场营销数据  marketing 为 true 时 使用 */
					{
						"startTime": "",        /*!< 开始时间戳 */
						"endTime": "",          /*!< 结束时间戳 */
						"beforeImgUrl": "",     /*!< 活动前图片 */
						"beforeActionUrl": "",  /*!< 活动前点击事件URL */
						"ingImgUrl": "",        /*!< 活动中图片 */
						"ingActionUrl": "",     /*!< 活动中点击事件URL */
						"afterImgUrl": "",      /*!< 活动后图片 */
						"afterActionUrl": "",   /*!< 活动后点击事件URL */
					}  		
				}
		},{
			//TQHomeStyleInfo 模型的 DTO
		}
		//......
	]
}
```

## 示例

`PS: 猜你喜欢为服务端查表数据，与后台配置数据区分，单独字段，不以 style 区分`

#### 1.banner (375x190)  `style 1`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/1.png)

```
{	
	"style" : 1,
	"info" : "banner",
	"contentList" : [
		{
          "picUrl" : "图片URL",
          "actionUrl" : "点击事件"
        },{
          "picUrl" : "图片URL",
          "actionUrl" : "点击事件"
        }
    ]
}
```
---

#### 2.豆腐块导航 (icon图片比例  94x68) `style 2`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/2.png)

```
{
		"style" : 2,
		"info" : "豆腐块",
		"contentList" : [{
				"title" : 	"文字",
				"iconUrl" : "图片URL",
				"actionUrl" :  "点击事件"
			},{
				"title" : 	"文字",
				"iconUrl" : "图片URL",
				"actionUrl" :  "点击事件"
			},{
				"title" : 	"文字",
				"iconUrl" : "图片URL",
				"actionUrl" :  "点击事件"
			},{
				"title" : 	"文字",
				"iconUrl" : "图片URL",
				"actionUrl" :  "点击事件"
			}]	
		}
```
---

#### 3.品牌首付导航 `style 3`

`一行4个，图片可选`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/3.png)

```
{
		"style" : 3,
		"info" : "品牌首付导航",
		"contentList" : [{
				"title" : 	"文字",
				"iconUrl" : "图片URL",
				"actionUrl" :  "点击事件"
			},{
				"title" : 	"文字",
				"actionUrl" :  "点击事件"
			},{
				"title" : 	"文字",
				"iconUrl" : "图片URL",
				"actionUrl" :  "点击事件"
			},{
				"title" : 	"文字",
				"actionUrl" :  "点击事件"
			}]	
		}
```

---

#### 4.登记线索  `style 4`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/16.png)

```
{
		"style" : 4,
		"info" : "首页线索登记模块",
		"contentInfo" : {
				"color" : "184,233,134,1",
				"iconUrl" : "按钮图片URL"
			}	
		}
```

---

#### 5.活动倒计时模块  （宽高走配置）`style 5`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/15.png)

```
{
	"style" : 5,
	"info" : "首页活动倒计时模块",
	"contentInfo" : {
		"width": 750,            /*!< 图片宽 动态设置模块大小时用到 */
		"height": 190,           /*!< 图片高 动态设置模块大小时用到 */
		"marketing": true,     	/*!< 是否有营销活动 倒计时 */
		"marketInfo": 			/*!< 市场营销数据  marketing 为 true 时 使用 */
		{
			"startTime" : "开始时间戳",	
			"endTime" : "结束时间戳",
			"beforeImgUrl" : "活动前图片",
			"beforeActionUrl" : "活动前点击事件",
			"ingImgUrl" : "活动中图片URL",
			"ingActionUrl" : "活动中点击事件",
			"afterImgUrl" : "活动后图片URL",
			"afterActionUrl" : "活动后点击事件"
		}
	
	}	
}
```

---

#### 6.平台介绍滚动模块  (前面图片大小 114x44) `style 6`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/17.png)

```
	{
			"style" : 6,
			"info" : "平台介绍滚动条",
			"moduleImgUrl" : "平台介绍前面图片， 固定尺寸", 
			"contentList" : [{
				"title" : "文字",
				"actionUrl" : "点击事件"
			},{
				"title" : "文字",
				"actionUrl" : "点击事件"
			}]
		}
```

---

#### 7.淘汽话题 `style 7`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/5.png)

```
{
	"style" : 7,
	"info" : "淘汽话题滚动条",
	"moduleImgUrl" : "淘汽话题前面图片， 固定尺寸", 
	"contentList" : [{
		"title" : "文字",
		"iconUrl" : "右边的图片",
		"actionUrl" : "点击事件"
	},{
		"title" : "文字",
		"iconUrl" : "右边的图片",
		"actionUrl" : "点击事件"
	}]
}
```

---

#### 8.无边距单图模块  (宽高走配置) `style 8`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/4.png)

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/13.png)

```
{
		"style" : 8,
		"info" : "无边距单图模块",
		"contentInfo" : {
			"actionUrl" : "点击事件",
			"picUrl" : "图片URL",
			"width" : "759",
			"height" : "198"
		}	
	}
```

---

#### 9.有边距固定大小单图模块  `style 9`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/18.png)

```
{
		"style" : 9,
		"info" : "有边距固定大小单图模块",
		"contentInfo" : {
			"actionUrl" : "点击事件",
			"picUrl" : "图片URL",
		}	
	}
```

---
#### 10.小banner (375x190) `style 10`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/7.png)

```
{	
	"style" : 10,
	"info" : "小 banner",
	"contentList" : [
		{
          "picUrl" : "图片URL",
          "actionUrl" : "点击事件"
        },{
          "picUrl" : "图片URL",
          "actionUrl" : "点击事件"
        }
    ]
}
```

---
#### 11.多行横向滚动样式 (375x190) `style 11`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/8.png)

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/19.png)

```
{	
	"style" : 11,
	"info" : "多行横向滚动样式",
	"contentScrollList" : [
		[{
          "picUrl" : "图片URL",
          "actionUrl" : "点击事件"
        },{
          "picUrl" : "图片URL",
          "actionUrl" : "点击事件"
        },{
          "picUrl" : "图片URL",
          "actionUrl" : "点击事件"
        },{
          "picUrl" : "图片URL",
          "actionUrl" : "点击事件"
        }
		],[
		{
          "picUrl" : "图片URL",
          "actionUrl" : "点击事件"
        },{
          "picUrl" : "图片URL",
          "actionUrl" : "点击事件"
        }
		]
    ]
}
```

---
#### 12.两列多行样式 (375x190) `style 12`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/9.png)

```
{	
	"style" : 12,
	"info" : "两列多行样式",
	"contentList" : [
		{
          "picUrl" : "图片URL",
          "tagUrl" : "标签url",
          "actionUrl" : "点击事件"
        },{
          "picUrl" : "图片URL",
          "actionUrl" : "点击事件"
        },{
          "picUrl" : "图片URL",
          "actionUrl" : "点击事件"
        },{
          "picUrl" : "图片URL",
          "actionUrl" : "点击事件"
        }
    ]
}
```

---
#### 31.豆腐块样式1  (3格子) `style 31`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/30.png)

#### 32.豆腐块样式2  (3格子) `style 32`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/31.png)

#### 33.豆腐块样式3  (4格子) `style 33`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/32.png)

#### 34.豆腐块样式4  (4格子) `style 34`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/33.png)

#### 35.豆腐块样式5  (4格子) `style 35`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/34.png)

#### 36.豆腐块样式6  (5格子) `style 36`

![image](https://github.com/mk2016/XianZhiProject/blob/master/Resource/image/35.png)

```
{
	"style" : 31,		//31-36
	"info" : "车辆导购豆腐块",
	"contentList" : [		//列表数据 数量 对应样式 格子数量
		{
			"tagUrl" : "标签图片",
			"marketing" : true,		//是否有营销 倒计时， true 时，使用 marketInfo 内的配置
			"marketInfo" : {		//营销信息配置
				"startTime" : "开始时间戳",	
				"endTime" : "结束时间戳",
				"beforeImgUrl" : "活动前图片",
				"beforeActionUrl" : "活动前点击事件",
				"ingImgUrl" : "活动中图片URL",
				"ingActionUrl" : "活动中点击事件",
				"afterImgUrl" : "活动后图片URL",
				"afterActionUrl" : "活动后点击事件"
			}				
		},{
			"picUrl" : "图片URL",
			"tagUrl" : "标签图片",			
			"actionUrl" : "点击事件"
		},{
			"picUrl" : "图片URL",
			"actionUrl" : "点击事件"
		},{
			"picUrl" : "图片URL",
			"tagUrl" : "标签图片",		
			"actionUrl" : "点击事件"
		}
	]
}
```

---
#### 40.分割线 `style 40`

```
{	
	"style" : 40,
	"info" : "分割线"
}
```

#### 41.分割条 `style 41`

```
{	
	"style" : 41,
	"info" : "分割条"
}
```

---
#### 车主晒单 （这期不做）
#### 淘汽问答	（这期不做）
