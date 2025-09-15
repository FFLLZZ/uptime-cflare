<div align="right">
  <a title="English" href="README.md"><img src="https://img.shields.io/badge/-English-A31F34?style=for-the-badge" alt="English" /></a>
  <a title="简体中文" href="README_zh-CN.md"><img src="https://img.shields.io/badge/-%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87-545759?style=for-the-badge" alt="简体中文"></a>
</div>

# ✔[UptimeFlare](https://github.com/amclubs/am-uptime-flare/)

A more advanced, serverless, and free uptime monitoring & status page solution, powered by Cloudflare Workers, complete with a user-friendly interface.

# 视频教程
- [点击进入视频教程](https://youtu.be/X03S2HxnniM)

- [serv00所有视频教程](https://www.youtube.com/playlist?list=PLGVQi7TjHKXaVlrHP9Du61CaEThYCQaiY)


创建Cloudflare TOKEN 用于github部署用

创建链接： https://dash.cloudflare.com/profile/api-tokens


点击创建令牌,选择 编辑 Cloudflare Workers 模板,然后将 帐户资源 设置为自己的账户。 区域资源 设置为 所有区域

部署uptime-flare

设置 SECRET

① 点击 settings -> secrets and variables -> new repo secret

② Name 的值是 CLOUDFLARE_API_TOKEN

③ Secret 的值是在CF获得的 Token 值


3、修改 uptime.config.ts 文件

① 修改 PageConfig 配置里的Links数组,这是监控首页的站点显示信,不是监控的站点,如

links: [
  { link: 'https://xxx.809098.xyz', label: '个人博客' },
  { link: 'https://888888.xyz', label: 'Blog', highlight: true },
]

② 修改 WorkConfig 配置,里面是要监控的站点

monitors: [
    {
      id: 'xxxx.809098.xyz',
      name: '个人博客',
      method: 'GET',
      target: 'https://xxxxx.809098.xyz',
      tooltip: 'My production server monitor',
      statusPageLink: 'https://xxxxx.809098.xyz',
      timeout: 10000,
    },
],	

③ 在github的actions看部署成功,就完成了部署

④ 在 Cloudflare 里就可以看到一个page项目 uptimeflare ,可以自己绑定域名,用域名来访问
  



## ⭐Features
- Open-source, easy to deploy (in under 10 minutes, no local tools required), and free
- Monitoring capabilities
  - Up to 50 checks at 1-minute intervals
  - Geo-specific checks from over [310 cities](https://www.cloudflare.com/network/) worldwide
  - Support for HTTP/HTTPS/TCP port monitoring
  - Up to 90-day uptime history and uptime percentage tracking
  - Customizable request methods, headers, and body for HTTP(s)
  - Custom status code & keyword checks for HTTP(s)
  - Downtime notification supporting [100+ notification channels](https://github.com/caronc/apprise/wiki)
  - Customizable Webhook
- Status page
  - Interactive ping (response time) chart for all types of monitors
  - Responsive UI that adapts to your system theme
  - Customizable status page
  - Use your own domain with CNAME
  - Optional password authentication (private status page)
  - JSON API for fetching realtime status data

## 👀Demo

My status page (Online demo): https://uptimeflare.amclubss.us.kg/

Some screenshots:

![Desktop, Light theme](docs/desktop.png)

## ⚡Quickstart / 📄Documentation

Please refer to [Wiki](https://github.com/lyc8503/UptimeFlare/wiki)

## New features (TODOs)

- [x] Specify region for monitors
- [x] TCP `opened` promise
- [x] Use apprise to support various notification channels
- [x] ~~Telegram example~~
- [x] ~~[Bark](https://bark.day.app) example~~
- [x] ~~Email notification via Cloudflare Email Workers~~
- [x] Improve docs by providing simple examples
- [x] Notification grace period
- [ ] SSL certificate checks
- [ ] Self-host Dockerfile
- [ ] Incident timeline
- [ ] Improve `checkLocationWorkerRoute` and fix possible `proxy failed`
- [ ] Groups 
- [x] Remove old incidents
