---

date: "2020-10-18T22:11:05+08:00"

title: "hugo网站配置聊天"

tags: ["dao"]

categories: ["dao"]

---



## 地址 

http://dashboard.daovoice.io



## 配置

注册 

运用设置 复制到头部

```
<script>(function(i,s,o,g,r,a,m){i["DaoVoiceObject"]=r;i[r]=i[r]||function(){(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;a.charset="utf-8";m.parentNode.insertBefore(a,m)})(window,document,"script",('https:' == document.location.protocol ? 'https:' : 'http:') + "//widget.daovoice.io/widget/9e961453.js","daovoice")</script>
```

复制到末尾

```
<script>
daovoice('init', {
  app_id: "9e961453"
});
daovoice('update');
</script>
```



hugo 复制第一个到 themes/layouts/partials/head.html

hugo 复制第二个到 themes/layouts/partials/footer.html