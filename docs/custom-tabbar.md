# 自定义tabbar

官方例子在这[link](https://developers.weixin.qq.com/miniprogram/dev/framework/ability/custom-tabbar.html)

主要的坑在于，`custom-tab-bar/index.js`里的这段代码具有迷惑性

```js
switchTab(e) {
    const data = e.currentTarget.dataset
    const url = data.path
    wx.switchTab({url})
    this.setData({
        selected: data.index
    })
}

```

这里对`selected`进行赋值是多余的。因为例子实际上实在具体的tab页面设置`selected`。


`pages/index/index.js`
```js
onShow() {
    if (typeof this.getTabBar === 'function' &&
      this.getTabBar()) {
      this.getTabBar().setData({
        selected: 0
      })
    }
  },
```



