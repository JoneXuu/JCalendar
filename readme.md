## 运行截图

[![运行截图](https://s1.ax1x.com/2022/06/23/jCCrrR.png)](https://imgtu.com/i/jCCrrR)
[![运行截图](https://s1.ax1x.com/2022/06/23/jCCDM9.png)](https://imgtu.com/i/jCCDM9)

# 主要功能
### 实测适配微信小程序、ios/android真机、H5

**签到**  
* 当天签到

**补签**  
* 过去的日期补签
* 红点标识漏签

**新增**  
* 双语支持
* 动态开启补签
* UI面板利用上下月日期补齐空格功能

## Github

组件代码很简单，注释也很全，期待你的Start！ [Github地址](https://github.com/JoneXuu/JCalendar).

## 使用示例

```
JS
	import JCalendar from '@/components/j-calendar.vue';
	export default {
		components: {
			JCalendar
		},
	}
HTML	
	<JCalendar :yearMonth="targetDate" :dataSource="signData"
	 @dateChange="refeshSignData($event)" @clickChange="updateSign($event)" >
	</JCalendar>
```
## 参数/函数
| 参数  | 描述 | 必填| 默认值（类型） |
| ------------- |:-------------:|:-------------:|:-------------:|
| isReplenishSign | 是否开启补签功能 | 否 | False(Boolean) |
| isFullCalendar | 是否需要填满日历功能，本月第一天是周3，那么UI面板前三格会是空的，开启则会用上月末尾的日期补齐空缺，结尾同理 | 否 |False (Boolean) |
| yearMonth | 指定日历面板的年月，“YYYY-MM”格式 | 否 | 当前年月 (String) |
| dataSource | 已经签到的数据源,例：["2022-01-05","2022-01-06"]表示5、6号已签到，兼容个位数前可加可不加0 | 是 | 空数组 (Array< Object >) |
| langType | 控制页面中英文，“ch”或“en” | 否 | ch (String) |
| （回调函数）clickChange | 点击签到或补签，回调参格式“YYYY-MM-DD” | 否 | - (String) |
| （回调函数）dateChange | 点击切换月份，回调参格式“YYYY-MM” | 否 | - (String) |
<style>
    /*这个是控制table的样式*/
    table th:nth-of-type(2) {
        width: 40%;
    }
</style>

## 说明
>打卡成功后需要你`同步数据给数据库`，切换月或重新进入页面再向数据库读取记录
(不会的建议参考我的Demo,而不是单独下个组件过来瞎折腾)。本地打卡不做任何记录，`仅仅模拟成功`
>>Hbuilder在为了大家伙不断成长迭代变得更优秀，所以此组件可能未能做到实时更新适配，特殊情况需要各位自己动动小手，一起让组件更Perfect~.


