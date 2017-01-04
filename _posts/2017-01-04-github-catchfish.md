---
layout: post

title:  “你们要的红包.lua"

date:   2017-01-04 12:43:08 +0800

tags: 实用小工具
---
# 缘由
前段时间刚好别人让我找找可用微信抢红包的代码，翻翻网盘里都是写老旧的玩意估计漏洞都被封了，最近也很忙偶尔看到小扳手这个工具想想就利用它做个穷举的函数监听得了！     

# talk is cheap,show the code   

## CatchFish.sh       

   
   
```bash    
    while true; do lua briberymoney.lua adb_weixin_lucky_money; done  
```    


## briberymoney.lua   

```lua
    adb_weixin_lucky_money = function ()
   while true do
      adb_shell("am start -n com.tencent.mm/com.tencent.mm.ui.LauncherUI")
      local w = adb_focused_window()
      if w ~= "com.tencent.mm/com.tencent.mm.ui.LauncherUI" then
         adb_event("key back key back")
      end
      adb_event("adb-tap 106 178 adb-tap 173 1862 adb-tap 375 340")
      adb_event("adb-tap 378 1572")
      local w = adb_focused_window()
      if w == "com.tencent.mm/com.tencent.mm.plugin.luckymoney.ui.LuckyMoneyReceiveUI" then
         adb_event("adb-tap 523 1263 sleep 1 key back")
      else
         adb_event("key back adb-tap 304 510 adb-tap 378 1572")
         w = adb_focused_window()
         if w == "com.tencent.mm/com.tencent.mm.plugin.luckymoney.ui.LuckyMoneyReceiveUI" then
            adb_event("adb-tap 523 1263 sleep 1 key back")
         end
      end
   end
end
```    

## 配置环境   

- 微信小扳手   

- android手机打开开发者模式支持调试（iphone党自行研究小扳手也有mac版）   

- linux环境,windows请自行配置cygwin    

# 告诫
抢红包游戏而已,光抢不发就有违初衷了- -！！
