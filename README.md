[English](README.english.md)

# schengen-chrome-extension

### 使用步骤

1. [下载最新版 chrome 扩展](https://github.com/visa-lol/schengen-chrome-extension/releases), 加载到自己的 chrome 里面
2. 到 [我们的网站](https://vis.lol/) 提交请求, 系统会自动创建一个 token 通过邮件回复给你
3. 把 token 输入到 chrome 扩展里面, 点击开始, 程序会自动运行, 不需要人工操作
4. 保持电脑开启
5. (可选) 如果担心 cloudflare 等验证码会弹出来, 影响到预约, 可以考虑安装一个 [nopecha chrome 扩展](https://nopecha.com/chrome), 它会帮你自动通过验证

### 程序工作原理

程序分两个部分
1. 客户端 (也就是你刚刚下载的 chrome 扩展):
   1. 定期刷新 Personal Center 页面的方式保持在线状态, 以便有 slot 的时候可以第一时间去预约, 而不需要登陆
   2. 接收来自于服务端的指令, 并执行
      1. 获取 slots, 发送给服务端 (最多 10 分钟获取一次, 取决于在线人数, 人越多间隔时间越长, 被封号的机率越低)
      2. 预约, 成功后发送预约到的 slot 给服务端
2. 服务端:
   1. 根据在线人数进行智能调度, 定期让不同的客户端获取 slots
   2. 拿到 slots 之后, 判断是否符合某些用户的要求, 如果符合, 发指令给这些客户端, 让它进行预约
   3. 收到客户端成功预约的消息, 给用户发邮件通知, 让用户尽快支付, 因为一小时就过期了

### 分析

根据工作原理来看, 如果有
1. 60 个活跃的客户端, 那么程序会每 10 秒让一个客户端去获取 slots, 每个客户端 10 分钟获取一次 slots
2. 300 个活跃的客户端, 那么程序会每 2 秒让一个客户端去获取 slots, 每个客户端 10 分钟获取一次 slots
3. 600 个活跃的客户端, 那么程序会每 1 秒让一个客户端去获取 slots, 每个客户端 10 分钟获取一次 slots
4. 900 个活跃的客户端, 那么程序会每 1 秒让一个客户端去获取 slots, 每个客户端 15 分钟获取一次 slots (因为服务端控制了最多每秒让一个客户端获取 slots, 没必要间隔太短)

一个帐号不可能每几秒刷新一次, 去获取 slots, 因为很容易被封号, 我知道有不少人用 Auto Refresh 浏览器扩展定期刷新, 被封号的

所以必须要有一个服务端进行智能的调度, 唯有集中所有人的力量, 才能打败黄牛, 等到没有黄牛的那天, 大家手动就能预约到

### 作为普通用户, 大家可以做什么?

#### 宣传
用各种方式宣传 (发小红书笔记等等), 让大家知道有这个项目, 用的人越多, 黄牛越没有立锥之地

#### 捐赠
如果觉得这个项目对你有帮助, 或者觉得它有 make the world a better place, 可以考虑捐赠支持, 因为
1. 这些签证网站经常改动, 维护更新代码需要耗费我大量个人时间精力
2. 维持服务端运行需要成本
3. 大家讨厌黄牛, 不想几个月后再次办签证的时候迫不得已去找黄牛

<img src="https://usvisa.lol/tips.png" width="250">
