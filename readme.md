# Checkin 功能介绍

通过 GitHub Actions 实现 [GLaDOS](https://glados.rocks/) 自动签到

# 使用说明

1. Fork 这个仓库

2. 登录 [GLaDOS](https://glados.rocks/)

3. 按 F12 打开开发者控制台，在 Headers 中找到 Cookie 以及 User-Agent，下面要用，Cookie 形如 gld:accts=gld_c9a6; gld:accts.sig=Z73e; gld:sess=gld_c9ac; gld:sess.sig=zYMl

4. 打开仓库的 Settings -> Secrets and variables -> Actions，设置 Repository secrets，`GLADOS = 上面获取的 Cookie`，`GLADOS_UA = 上面获取的 User-Agent`

5. 启用 Actions

# 高级功能

1. 如需修改时间, 可以修改文件 [run.yml](.github/workflows/run.yml#L7) 中的 `cron` 参数, 格式可参考 [crontab]

2. 如有多个帐号, 可以写为多行 Secret `GLADOS`, 每行写一个 Cookie

3. 满 500 积分自动兑换天数，如需开启 / 关闭，可以修改 Secret `AUTO_EXCHANGE` 为 true / false，如需修改兑换阈值，可以修改 Secret `EXCHANGE_THRESHOLD`，其默认值为 500

4. 如需更换其他域名, 可配置 Secret `DOMAIN`, 可填写: `railgun.info`

5. 如需推送通知, 可配置 Secret `NOTIFY`, 已支持:
    1. [WxPusher][wxpusher]: 格式 `wxpusher:{token}:{uid}`
    1. [PushPlus][pushplus]: 格式 `pushplus:{token}`
    1. [Bark][finbbark]: 格式 `bark:{key}`
    1. [企业微信][qyweixin]: 格式 `qyweixin:{key}`
    1. Console: 格式 `console:log`, 作为日志输出, 一般用于调试
    1. 如需配置多个, 可以写为多行, 每行写一个

[glados]: https://github.com/glados-network/GLaDOS
[crontab]: https://crontab.guru/
[pushplus]: https://www.pushplus.plus/
[wxpusher]: https://wxpusher.zjiecode.com/
[finbbark]: https://github.com/Finb/Bark
[qyweixin]: https://developer.work.weixin.qq.com/document/path/91770
