# 轮播图

## 实现方式

1.创建一个区域设置overflow:hidden(隐藏溢出)
2.将精灵图（或者通过相对定位)设置一排图在展示页面上
3.移动图片的位置
4.圆点则通过setInterval(定时器)来实现
5.通过animation-delay推迟动画时间促使圆点与画面近似于同步.
6.设置左右箭头调整移动方向，通过监听器进行监听
7.为了使画面无缝链接，需要五张图片12341,这样动画结束恢复原位就实现了复原。
