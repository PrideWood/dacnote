#### 40 OB 内右键查字典

插件：Search on Internet
以使用搜狗汉语为例，在插件设置打开 iframe 开关，无需离开 OB，添加 URL，并稍加改动

```
https://hanyu.sogou.com/result?query={{query}}
```

同理可添加百度词典、必应词典等，只是这两在更改 URL 时后面删除的多余的部分多一些。
使用 CSS 代码对 iframe 进行简单美化

```
iframe.soi-site {  
position: absolute;  
top: 35px;  
left: 0;  
width: 100%;  
height: 100%;  
border: 0;  
}
```

评论区
> 刚想弄一个日语词典，我一看我常用的 moji 辞书是这样的 https://www.mojidict.com/details/198935921 ，有什么办法吗？ *@o 顿顿 o*
> > https://www.mojidict.com/searchText/何となく 我看它这样也可以搜啊 *@Johnny 学*