+++

title = "20180719 Hugo+github 建立個人部落格心得分享"
date = 2018-07-19T15:00:00+08:00
draft = false

# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = ["Jimmy Kuo"]

# Tags and categories
# For example, use `tags = []` for no tags, or the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = ["hugo"]
categories = ["learning notes"]

# Featured image
# Place your image in the `static/img/` folder and reference its filename below, e.g. `image = "example.jpg"`.
# Use `caption` to display an image caption.
#   Markdown linking is allowed, e.g. `caption = "[Image credit](http://example.org)"`.
# Set `preview` to `false` to disable the thumbnail in listings.
[header]
image = "static/img/disquz.png"
caption = ""
preview = true

+++

# 20180719 Hugo+github 建立個人部落格心得分享

如果想要自己架網頁，可是沒有錢買網路主機，利用Github + Hugo絕對是你第一個選項！

因為很多人寫分享文，所以我直接留下連結，請大家按照步驟完成即可，這篇文章主要分享採雷過程。

基礎教學網頁：
* [在 GitHub 部署 Hugo 靜態網站](https://chswei.github.io/post/hugo/)
* [此文採用的Theme - academic](https://github.com/gcushen/hugo-academic/blob/master/exampleSite/config.toml)

注意：一切以這主題為出發點
--------------------------
1. 第一個雷：我用的主題(theme)與部落格主範例不一樣，一開始無論如何我的文章都無法順利的render出來，後來發現不是檔案問題，而是路徑問題或者更明確的說是資料夾名稱問題。Hugo quickstart官方文件有一段 ''hugo new posts/my-first-post.md'' 生成文章的語法，但是在很多的主題中，他指定的資料夾是''post/''，一個字的差別就會讓你**debug**到哭.
* [解法](https://github.com/gcushen/hugo-academic/blob/master/exampleSite/config.toml)

2. 第二個雷：沒有將主題必要的資料複製到Hugo專案中，網頁肯定沒辦法正常render。
* 解法：將想採用的主題中的static和layouts 直接取代Hugo專案根目錄中的同名資料夾（static和layouts）

3. 第三個雷：明明教學頁面有好多Menu可以點選，我的為什麼無法正常連結。
* 解法：content 資料夾要產生對應的資料夾名稱，比如說 post的按鈕就要對應產生"post資料夾"，且指定路徑為/post/，請以此類推。

4. 第四個雷:記得命名repository為{你想要名字}.github.io，不然一輩子也不會變成github page..

5. Hugo強大之處在於即時查看修改的結果，但改config檔有時候local server沒即時更改結果， 試試看斷線重啟server，或許可以有好的結果。

加入評論功能
---------------------------
[本文採用Disqus : 還有其他可以選擇](https://disqus.com/)

[Hugo Comments 官方設定教學](https://gohugo.io/content-management/comments/)

1. 第一個雷： 我明明在toml檔中加入'' disqusShortname = "yourdiscussshortname" ''，可是還是沒有留言框出現，鑲嵌出了問題怎辦？
* 解法：進入你的disquz帳號->選取setting->installation->點選如下圖連結
 ![](https://i.imgur.com/raysFVi.png)
 會產生以下程式碼，並將之複製且覆蓋hugo專案的layouts/partials/comments.html中，即可以解決此問題。
![](https://i.imgur.com/UHllbsh.png)

-----------------------

提醒：各個主題通常會有exampleSite的說明範例，務必詳細閱讀，因為每個的規則都不太一樣，所以此文可能只能解決這主題的問題。

