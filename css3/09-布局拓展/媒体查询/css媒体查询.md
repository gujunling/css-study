### css3 媒体查询是响应式的核心


#### 媒体类型

```
all            所有媒体
screen         彩色屏幕
print          打印预览
```

#### 媒体属性

```
浏览器视口尺寸  width			           （可加max min前缀）
浏览器视口尺寸 height			         （可加max min前缀）
设备独立像素（pc端：分辨率； 移动端：具体看机器的参数）：device-width	       （可加max min前缀）
设备像素比（pc端：1；  移动端：具体看机器参数） -webkit-device-pixel-ratio   （可加max min前缀，需要加webkit前缀）
orientation     portrait竖屏/landscape横屏
```

#### 关键字

```
and ：代表与的意思，一般用and来连接媒体类型和媒体属性

only ： 和浏览器的兼容性有关，防止老旧的浏览器  不支持带媒体属性的查询而应用到给定的样式。
                在老款的浏览器下
                @media only    --->    因为没有only这种设备 规则被忽略
                @media screen --->   因为有screen这种设备而且老浏览器会忽略带媒体属性的查询
                
(,) : 代表或者的意思，对于所有的连接选项只要匹配成功一个就能应用规则

not: 代表取反的意思，
```

